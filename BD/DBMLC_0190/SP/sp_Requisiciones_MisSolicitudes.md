# Stored Procedure: sp_Requisiciones_MisSolicitudes

## Usa los objetos:
- [[Cargos]]
- [[Profiles]]
- [[Requisiciones_Cargos]]
- [[Requisiciones_Estados]]
- [[Requisiciones_EstadosNomina]]
- [[Requisiciones_EstadosReclutador]]
- [[Requisiciones_Solicitudes]]
- [[Requisiciones_SolicitudesCandidatos]]
- [[Requisiciones_SolicitudesEsquema]]
- [[Requisiciones_SolicitudProveedor]]
- [[v_Requisiciones_CiudadDepto]]
- [[v_Requisiciones_Observaciones_Nomina]]
- [[v_Requisiciones_Observaciones_Solicitud]]
- [[v_Requisiciones_ParametrizacionTipoValor]]
- [[vw_DiasFestivos]]

```sql
CREATE PROC [dbo].[sp_Requisiciones_MisSolicitudes] 
(
	@UserId NVARCHAR(50),
	@Estado BIT
)AS

BEGIN
	
	SET NOCOUNT ON
	SET FMTONLY OFF

	--DECLARE @UserId NVARCHAR(50), @Estado BIT;
	--SET @UserId = 'df8e3e59-db1a-4a5f-a030-acafae6d7ab8'
	--SET @Estado = 0

	DECLARE @TipoEstado NVARCHAR(15);

	IF @Estado = 1
		BEGIN 
			SET @TipoEstado = 'ABIERTO';
		END
	
	ELSE
		BEGIN 
			SET @TipoEstado = 'CERRADO';
		END
	


	SELECT	DISTINCT								Numero_solicitud,					Estado,								DetalleEstado,
		TipoSolicitud,								NITProveedor,						FechaAutorizacionGteLinea,			FechaCreacion,
		CodigoCargo,								NombreCargo,						CargoCritico,						Salario,
		IdSolicitante,								Solicitante,						CodEmpresa,							Empresa,
		CodMarca,									Marca,								CodCentro,							Centro,
		CodigoUnidadNegocio,						UnidadNegocio,						CodSeccion,							Seccion,
		CodDepartamento,							Departamento,						CodSede,							Sede,
		Unica,										Observaciones,						IdEstadoReclutador,					EstadoReclutador,
		IdEstadoNomina,								EstadoNomina,						FechaInicioContrato,				FechaCitacionFirmaContrato,
		FechaCitacionFirmaContratoAplazada,			tip_con,							nom_con,							DuracionContratoMeses,
		BonoAlimentacion,							BonoCelular,						BonoGasolina,						AuxMovilizacion,
		SalarioGarantizado,							FinSalario,							DescripcionTrabajo,					Requisitos,
		PrimerEsquema,								SegundoEsquema,						TercerEsquema,						CuartoEsquema,
		QuintoEsquema,								SextoEsquema,						ObservacionesGteUSC,				ObservacionesGteLinea,
		ObservacionesCancelacionSolicitud,			CandidatoNoFirmaContrato,			CandidatoDevueltoSeleccion,			CandidatoAplazaFirmaContrato,
		JefeAplazaFirmaContrato,					CancelacionInactividad,				Candidatos_PendienteEntrevista,		Candidatos_Entrevistado,
		Candidatos_Potencial,						Candidatos_Seleccionado,			Candidatos_Rechazados,				Candidatos_Preseleccionado,
		Candidatos_DevueltoSeleccion,				Candidatos_Contratados,				HorarioDiurno,						Horario,
		EstadoGeneral,								DescEstadoGeneral,					CodCiudadLabor,						NombreCiudadLabor,
		InHouse,									InHouseProyect,						InHouseNombreProyect,				InHouseConfir,
		TipoProceso,								NuevoSalario,
		TiempoTranscurrido = CASE WHEN CONVERT(DATE,FechaCreacion) = CONVERT(DATE,GETDATE()) THEN 0
								  WHEN (TiempoTranscurrido - 1) < 0 THEN 0
								  ELSE (TiempoTranscurrido - 1) END
	FROM 						  
	(
		SELECT	DISTINCT				Numero_solicitud,			Estado,					DetalleEstado,				TipoSolicitud,
			NITProveedor,				FechaCreacion,				CodigoCargo,			NombreCargo,				CargoCritico,
			Salario,					IdSolicitante,				Solicitante,			CodEmpresa,					Empresa,
			CodMarca,					Marca,						CodCentro,				Centro,						CodigoUnidadNegocio,
			UnidadNegocio,				CodSeccion,					Seccion,				CodDepartamento,			Departamento,
			CodSede,					Sede,						Unica,					Observaciones,				IdEstadoReclutador,
			EstadoReclutador,			IdEstadoNomina,				EstadoNomina,			FechaInicioContrato,		FechaCitacionFirmaContrato,
			tip_con,					nom_con,					BonoCelular,			BonoAlimentacion,			DuracionContratoMeses,
			BonoGasolina,				AuxMovilizacion,			FinSalario,				SalarioGarantizado,			InHouseConfir,
			DescripcionTrabajo,			Requisitos,					PrimerEsquema,			SegundoEsquema,				TercerEsquema,	
			CuartoEsquema,				QuintoEsquema,				SextoEsquema,			ObservacionesGteUSC,		HorarioDiurno,
			EstadoGeneral,				DescEstadoGeneral,			CodCiudadLabor,			NombreCiudadLabor,			InHouse, 
			InHouseProyect,				InHouseNombreProyect,		TipoProceso,			NuevoSalario,
			
			ObservacionesGteLinea,					ObservacionesCancelacionSolicitud,		CandidatoNoFirmaContrato,
			CandidatoDevueltoSeleccion,				CandidatoAplazaFirmaContrato,			JefeAplazaFirmaContrato,
			Candidatos_PendienteEntrevista,			Candidatos_Entrevistado,				Candidatos_Potencial,
			Candidatos_Seleccionado,				Candidatos_Rechazados,					Candidatos_Preseleccionado,
			Candidatos_DevueltoSeleccion,			Candidatos_Contratados,					FechaCitacionFirmaContratoAplazada,
			CancelacionInactividad,
			
			FechaAutorizacionGteLinea=CONVERT(date,FechaAutorizacionGteLinea),
			
			Horario = CASE WHEN HorarioDiurno = 1 THEN 'Diurno' ELSE 'Nocturno' END, 
			
			'TiempoTranscurrido' = 
				(SELECT  SUM(CASE WHEN F.DiaSemana BETWEEN 1 AND 5 THEN F.Cant ELSE 0 END) - 
					(SELECT COUNT(Fechafestivo) FROM vw_DiasFestivos where Fechafestivo >= FechaAutorizacionGteLinea AND Fechafestivo <= GETDATE()) AS 'TiempoTranscurrido'
						FROM  (
							SELECT  1 AS Diasemana, DATEDIFF(DAY, -7, GETDATE())/7-DATEDIFF(DAY, -6, FechaAutorizacionGteLinea)/7 AS Cant UNION
							SELECT  2 AS Diasemana, DATEDIFF(DAY, -6, GETDATE())/7-DATEDIFF(DAY, -5, FechaAutorizacionGteLinea)/7 AS Cant UNION
							SELECT  3 AS Diasemana, DATEDIFF(DAY, -5, GETDATE())/7-DATEDIFF(DAY, -4, FechaAutorizacionGteLinea)/7 AS Cant UNION
							SELECT  4 AS Diasemana, DATEDIFF(DAY, -4, GETDATE())/7-DATEDIFF(DAY, -3, FechaAutorizacionGteLinea)/7 AS Cant UNION
							SELECT  5 AS Diasemana, DATEDIFF(DAY, -3, GETDATE())/7-DATEDIFF(DAY, -2, FechaAutorizacionGteLinea)/7 AS Cant UNION
							SELECT  6 AS Diasemana, DATEDIFF(DAY, -2, GETDATE())/7-DATEDIFF(DAY, -1, FechaAutorizacionGteLinea)/7 AS Cant UNION
							SELECT  7 AS Diasemana, DATEDIFF(DAY, -1, GETDATE())/7-DATEDIFF(DAY,  0, FechaAutorizacionGteLinea)/7 AS Cant	
						) F)
		FROM 
		(
			SELECT	DISTINCT						Estado=s.idEstado,					s.TipoSolicitud, 					s.CodigoCargo,			
				c.NombreCargo,						s.Salario,							s.CodEmpresa,						s.Empresa,
				s.CodMarca,							s.Marca,							s.CodCentro,						s.Centro,
				s.CodigoUnidadNegocio,				s.UnidadNegocio,					s.CodSeccion,						s.Seccion,
				s.CodDepartamento,					s.Departamento,						s.CodSede,							s.Sede,
				s.Unica,							s.IdEstadoNomina,					n.EstadoNomina,						s.tip_con,
				s.nom_con,							s.DuracionContratoMeses,			s.BonoAlimentacion,					s.BonoCelular,
				s.BonoGasolina,						s.AuxMovilizacion,					s.SalarioGarantizado,				s.FinSalario,
				s.DescripcionTrabajo,				s.Requisitos,						Esq.PrimerEsquema,					Esq.SegundoEsquema,
				Esq.TercerEsquema,					Esq.CuartoEsquema,					Esq.QuintoEsquema,					Esq.SextoEsquema,
				s.IdEstadoReclutador,				S.HorarioDiurno,					S.CodCiudadLabor, 					S.InHouse, 
				S.InHouseProyect,					E.TipoProceso,						S.NuevoSalario,

				InHouseNombreProyect = TV.Nombre,			Numero_solicitud = s.idsolicitud,		NombreCiudadLabor = Ciudad.NombreCiudad, 		
				DetalleEstado=e.Estado,						NITProveedor = ISNULL(sp.Nit, 0),		FechaCreacion = CONVERT(date,s.FechaCreacion),
				CargoCritico = ISNULL(CC.Critico,0),		IdSolicitante = p.UserId,				Solicitante = p.Nombres + ' ' + p.Apellidos,
				Observaciones = s.Observaciones,			s.FechaInicioContrato,					s.FechaCitacionFirmaContrato,
				s.FechaCitacionFirmaContratoAplazada,		EstadoReclutador = er.Estado, 			Con_can.Candidatos_PendienteEntrevista,			
						
				Con_can.Candidatos_Entrevistado,					JefeAplazaFirmaContrato=Obs_N.Observaciones_JefeAplazaFirma,
				Con_can.Candidatos_Potencial,						ObservacionesGteUSC=Obs_S.Observaciones_NuevoSalarioAceptado,
				Con_can.Candidatos_Seleccionado,					ObservacionesCancelacionSolicitud=Obs_S.Observaciones_Cancelada,
				Con_can.Candidatos_Preseleccionado,					CandidatoDevueltoSeleccion=Obs_N.Observaciones_DevueltoSeleccion,
				Con_can.Candidatos_Rechazados,						CancelacionInactividad=Obs_S.Observaciones_FinalizadaFaltaRespuesta,
				Con_can.Candidatos_Contratados,						CandidatoNoFirmaContrato=Obs_N.Observaciones_CandidatoNoFirmaContrato,
				Con_can.Candidatos_DevueltoSeleccion,				CandidatoAplazaFirmaContrato=Obs_N.Observaciones_CandidatoAplazaFirma,
						
				InHouseConfir = CASE WHEN InHouse = 1 THEN 'Si' ELSE 'No' END,

				FechaAutorizacionGteLinea = CASE WHEN Obs_S.Estado_PendienteAsociarProveedor IS NOT NULL 
												THEN Obs_S.Fecha_PendienteAsociarProveedor ELSE Obs_S.Fecha_BusquedaCandidatos END,

				ObservacionesGteLinea = CASE WHEN Obs_S.Estado_PendienteAsociarProveedor IS NOT NULL 
												THEN Obs_S.Observaciones_PendienteAsociarProveedor ELSE Obs_S.Observaciones_BusquedaCandidatos END,
						

				EstadoGeneral = CASE WHEN s.IdEstado = 2 AND s.IdEstadoReclutador IN (1,2,3,4,5,6) THEN er.Estado
										WHEN s.IdEstado = 3 AND s.IdEstadoNomina IN (5,6,8,9) THEN n.EstadoNomina
										ELSE e.Estado END,


				DescEstadoGeneral = CASE WHEN s.IdEstado = 2 AND s.IdEstadoReclutador IN (1,2,3,4,5,6) THEN er.Descripcion
										WHEN s.IdEstado = 3 AND s.IdEstadoNomina IN (5,6,8,9) THEN n.Descripcion
										ELSE e.Descripcion END
		
			FROM		Requisiciones_Solicitudes AS s

			LEFT JOIN   Requisiciones_Estados AS e ON s.IdEstado = e.IdEstado

			LEFT JOIN   Requisiciones_EstadosReclutador AS er ON s.IdEstadoReclutador = er.IdEstado

			LEFT JOIN	Requisiciones_EstadosNomina AS n ON s.IdEstadoNomina = n.IdEstadoNomina
					
			LEFT JOIN	v_Requisiciones_ParametrizacionTipoValor AS TV ON TV.Id = S.InHouseProyect AND TV.Tipo = 'InHouse'

			LEFT JOIN	v_Requisiciones_CiudadDepto AS Ciudad ON Ciudad.CodigoCiudad = S.CodCiudadLabor AND Ciudad.CodigoPais = '057'
					
			LEFT JOIN   Cargos AS c ON  c.CodigoCargo = s.CodigoCargo

			LEFT JOIN   Requisiciones_Cargos AS CC ON  cc.CodigoCargo = s.CodigoCargo and s.CodigoUnidadNegocio = CC.CodigoMarca

			LEFT JOIN   Profiles AS p ON s.UserIdCreo = p.UserId

			LEFT JOIN	
			(
				SELECT *
				FROM Requisiciones_SolicitudProveedor 
				WHERE Nit <> 0
			) AS sp ON s.IdSolicitud = sp.Solicitud

			--Observaciones Solicitud 
			LEFT JOIN v_Requisiciones_Observaciones_Solicitud AS Obs_S ON Obs_S.IdSolicitud = S.IdSolicitud

			--Observaciones Nomina 
			LEFT JOIN v_Requisiciones_Observaciones_Nomina AS Obs_N ON Obs_N.IdSolicitud = S.IdSolicitud

			--Consulta Esquemas Variables
			LEFT JOIN (
				SELECT  IdSolicitud,		
						PrimerEsquema = MAX(PrimerEsquema),			SegundoEsquema=MAX(SegundoEsquema),  
						TercerEsquema = MAX(TercerEsquema),			CuartoEsquema=MAX(CuartoEsquema),  
						QuintoEsquema = MAX(QuintoEsquema),			SextoEsquema=MAX(SextoEsquema)
		
				FROM
				(
					SELECT IdSolicitud, 
						CASE WHEN NumeroEsquema = 1 THEN Esquema ELSE NULL END AS PrimerEsquema,
						CASE WHEN NumeroEsquema = 2 THEN Esquema ELSE NULL END AS SegundoEsquema,
						CASE WHEN NumeroEsquema = 3 THEN Esquema ELSE NULL END AS TercerEsquema,
						CASE WHEN NumeroEsquema = 4 THEN Esquema ELSE NULL END AS CuartoEsquema,
						CASE WHEN NumeroEsquema = 5 THEN Esquema ELSE NULL END AS QuintoEsquema,
						CASE WHEN NumeroEsquema = 6 THEN Esquema ELSE NULL END AS SextoEsquema
					FROM Requisiciones_SolicitudesEsquema AS a
					WHERE Esquema IS NOT NULL AND LTRIM(RTRIM(Esquema)) <> ''
				) A
				GROUP BY IdSolicitud
			) Esq ON s.IdSolicitud = Esq.IdSolicitud
	
			LEFT JOIN --Cantidad de Candidatos anexados en la solicitud
			(
				SELECT DISTINCT IdSolicitud, 
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 1 AND IdSolicitud = a.IdSolicitud)Candidatos_PendienteEntrevista,
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 2 AND IdSolicitud = a.IdSolicitud)Candidatos_Entrevistado,
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 3 AND IdSolicitud = a.IdSolicitud)Candidatos_Potencial,
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 4 AND IdSolicitud = a.IdSolicitud)Candidatos_Seleccionado,
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 5 AND IdSolicitud = a.IdSolicitud)Candidatos_Rechazados,
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 6 AND IdSolicitud = a.IdSolicitud)Candidatos_Preseleccionado,
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 7 AND IdSolicitud = a.IdSolicitud)Candidatos_DevueltoSeleccion,
					(SELECT TOP(1) count(Cedula) FROM Requisiciones_SolicitudesCandidatos WHERE IdEstadoCandidato = 8 AND IdSolicitud = a.IdSolicitud)Candidatos_Contratados	
				FROM Requisiciones_SolicitudesCandidatos AS a
			) Con_can ON S.IdSolicitud = Con_can.IdSolicitud
			
		) AS A
		WHERE IdSolicitante = @UserId AND TipoProceso = @TipoEstado
	)A

END

```