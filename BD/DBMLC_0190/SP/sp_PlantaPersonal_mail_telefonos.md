# Stored Procedure: sp_PlantaPersonal_mail_telefonos

## Usa los objetos:
- [[CentrosDirecciones]]
- [[EmpleadosActivos]]
- [[gen_tipide]]
- [[Jerarquia_EmpleadosNoNomina]]
- [[JerarquiaEmpleados]]
- [[rhh_emplea]]
- [[rhh_tbfondos]]
- [[usr_rhh_telpersonas]]

```sql
--Sp Planta de personal 
CREATE PROCEDURE [dbo].[sp_PlantaPersonal_mail_telefonos] 
(
	@Ano as int,
	@Mes as int
) AS

BEGIN

--DECLARE @ano int, @mes int
--SET @ano=2023
--SET @mes=7

SELECT a.estado,                       a.CodigoEmpleado,                a.Empresa,                    Nombres= a.nombres + ' ' + a.Apellido1 + ' ' + a.Apellido2,
       a.Fecha_Ingreso,                a.Nombre_Unidad_Negocio,         a.Marca,	                  a.nombre_centro,
	   a.nombre_seccion,               a.Nombre_Sucursal,               a.nombre_departamento,        a.Nombre_Departamento_trabajo, 
	   a.Nombre_Cargo,                 a.Nombre_Ciudad_trabajo,         a.Email_Corporativo,          Email_personal=a.email,
	   Celular_Personal=a.Celular,     t.Cel_corporativo,               t.Fijo_corporativo,           TelefonoFijo_Personal=a.Telefono_fijo, 
	   t.Ext_corporativo,              t.Cel_personal,                  t.Fijo_personal,              d.Direccion,
	   e.gru_san,                      e.fac_rhh,                       TipoDocumento=i.des_tip,      NumeroDocumento=a.CodigoEmpleado,
	   Codigo_FondoRiesgos=e.fdo_ate,  Nombre_FondoRiesgos=ate.nom_fdo,	Porcentaje_Riesgos=e.por_ate, Codigo_FondoSalud =e.fdo_sal,
	   Nombre_FondoSalud=sal.nom_fdo,  Codigo_FondoPension=e.fdo_pen,   Nombre_FondoPensiones=pen.nom_fdo,
	   Genero = CASE WHEN e.sex_emp = 2 THEN 'M' 
	                 ELSE 'F' END,

	    case when je.Cedula IS null then ji.CodigoEmpleado
		     else je.Cedula end cc_jefe1 ,
		
		case when je.Nombre IS null then ji.Nombres+' '+ji.Apellido1+' '+ji.Apellido2 								
	         else je.Nombre end nombre_jefe

  FROM [DBMLC_0190].dbo.EmpleadosActivos a

  LEFT JOIN [Novasoft_CT_MM].dbo.usr_rhh_telpersonas   t ON	t.Empleado = a.CodigoEmpleado

  LEFT JOIN [Novasoft_CT_MM].dbo.rhh_emplea			   e ON	a.CodigoEmpleado = e.cod_emp 	
														AND a.Ano_Periodo = @ano 
														AND a.mes_periodo = @mes
  LEFT JOIN [DBMLC_0190].dbo.CentrosDirecciones        d ON a.codigo_centro = d.CodigoCentro 

  LEFT JOIN [Novasoft_CT_MM].dbo.gen_tipide			   i ON	i.cod_tip = e.tip_ide
													    AND a.Ano_Periodo = @ano 
														AND a.mes_periodo = @mes
  left join [DBMLC_0190].dbo.JerarquiaEmpleados        j on a.CodigoEmpleado = j.Cedula

  left join [DBMLC_0190].dbo.Jerarquia_EmpleadosNoNomina je on je.Cedula = j.cc_jefe1

  left join [DBMLC_0190].dbo.EmpleadosActivos         ji on ji.CodigoEmpleado =j.cc_jefe1
                                                        AND ji.Ano_Periodo = @ano 
														AND ji.mes_periodo = @mes
  left join [Novasoft_CT_MM].dbo.rhh_tbfondos       ate	 on ate.cod_fdo = e.fdo_ate
  left join [Novasoft_CT_MM].dbo.rhh_tbfondos   	sal  on sal.cod_fdo = e.fdo_sal
  left join [Novasoft_CT_MM].dbo.rhh_tbfondos   	pen  on	pen.cod_fdo = e.fdo_pen			

 WHERE a.Ano_Periodo = @ano 
   AND a.Mes_Periodo = @mes

END

```