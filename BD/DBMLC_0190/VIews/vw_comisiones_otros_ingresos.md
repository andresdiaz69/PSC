# View: vw_comisiones_otros_ingresos

## Usa los objetos:
- [[InformesDefinitivos]]
- [[InformesPresentaciones]]
- [[vw_InformesSedesCentros]]

```sql
create view [dbo].[vw_comisiones_otros_ingresos] as
--Otros Ingresos
Select distinct a.CodigoPresentacion,a.NombrePresentacion,Año=Año2,MesInicial=MesInicial2,MesFinal = MesFinal2,
CodigoConcepto,NombreConcepto,Sede,s.CodigoCentro,s.NombreCentro,Valor
from(
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede1,Valor=Actual1
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede2,Valor=Actual2
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede3,Valor=Actual3
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede4,Valor=Actual4
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede5,Valor=Actual5
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede6,Valor=Actual6
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede7,Valor=Actual7
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede8,Valor=Actual8
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede9,Valor=Actual9
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede10,Valor=Actual10
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede11,Valor=Actual11
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede12,Valor=Actual12
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede13,Valor=Actual13
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede14,Valor=Actual14
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede15,Valor=Actual15
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede16,Valor=Actual16
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede17,Valor=Actual17
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede18,Valor=Actual18
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede19,Valor=Actual19
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede20,Valor=Actual20
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede21,Valor=Actual21
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede22,Valor=Actual22
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede23,Valor=Actual23
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede24,Valor=Actual24
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
	union all
	select d.CodigoPresentacion,p.NombrePresentacion,Año2,MesInicial2,MesFinal2,Orden,Balance,
	Nivel1,Nivel2,Nivel3,Nivel4,Nivel5,Nivel6,CodigoConcepto,NombreConcepto,Sede=Sede25,Valor=Actual25
	from InformesComiteDB.dbo.InformesDefinitivos			d
	left join InformesComiteDB.dbo.InformesPresentaciones	p	on	d.CodigoPresentacion = p.CodigoPresentacion and d.balance = p.ArbolPYG 
	where d.balance = 17 
	and d.CodigoConcepto = 30004
) a		left join InformesComiteDB.dbo.vw_InformesSedesCentros	s	on	a.CodigoPresentacion = s.CodigoPresentacion
																		and a.sede = s.NombreSede
where Valor <> 0
and a.CodigoPresentacion = 5
and s.NombreCentro not like 'CO-%'
--and a.CodigoPresentacion = 5
--and a.año2 = 2020
--and a.MesFinal2 = 10
--and a.MesInicial2=10
--order by a.sede


```