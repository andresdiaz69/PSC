# View: v_GMF_10_ValoresVentasNetas_Colision

## Usa los objetos:
- [[InformesDefinitivosMes]]
- [[InformesPresentaciones]]
- [[vw_InformesSedesCentros]]

```sql
CREATE view [dbo].[v_GMF_10_ValoresVentasNetas_Colision] as
Select distinct Empresa=case when a.CodigoPresentacion in (1,6,7,8,9,12,28,87,88) then 1 else 6 end,
Marca = case	when s.nombreseccion like '%Dai-Bta- Auto norte%' then 'Daimler - Vehiculos'
				when s.nombreseccion like '%FR-%' then 'Ford'
				when s.nombreseccion like '%MZ-%' then 'Mazda'
				when s.nombreseccion like '%RN-%' then 'Renault'
				when s.nombreseccion like '%VW-%' then 'Volkswagen'
				else p.NombrePresentacion
		end,
a.CodigoPresentacion,p.nombrepresentacion,Año,Mes,CodigoConcepto,NombreConcepto,Sede,s.CodigoCentro,s.NombreCentro,s.NombreSeccion,Valor
from(
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede1,Valor = i.Actual1
		from [InformesComiteDB].dbo.[InformesDefinitivosMes]	i
		left join [InformesComiteDB].dbo.InformesPresentaciones					p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		----and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto in (18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.Sede2,Valor = i.Actual2
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede3,Valor = i.Actual3
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede4,Valor = i.Actual4
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede5,Valor = i.Actual5
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede6,Valor = i.Actual6
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede7,Valor = i.Actual7
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede8,Valor = i.Actual8
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede9,Valor = i.Actual9
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede10,Valor = i.Actual10
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede11,Valor = i.Actual11
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.Sede12,Valor = i.Actual12
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.Sede13,Valor = i.Actual13
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.Sede14,Valor = i.Actual14
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.Sede15,Valor = i.Actual15
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.Sede16,Valor = i.Actual16
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.Sede17,Valor = i.Actual17
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede18,Valor = i.Actual18
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede19,Valor = i.Actual19
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede20,Valor = i.Actual20
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede21,Valor = i.Actual21
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede22,Valor = i.Actual22
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede23,Valor = i.Actual23
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede24,Valor = i.Actual24
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
		union all
		select i.CodigoPresentacion,Año=i.Año2,Mes=i.MesFinal2,i.CodigoConcepto,i.NombreConcepto,
		Sede = i.sede25,Valor = i.Actual25
		from [InformesComiteDB].dbo.InformesDefinitivosMes			i
		left join [InformesComiteDB].dbo.InformesPresentaciones	p      on     i.CodigoPresentacion = p.CodigoPresentacion
		where i.CodigoPresentacion in (1,5,6,7,8,9,12,17,76,77,83)
		--and i.año2 = 2020
		--and i.mesfinal2 in (5)
		and i.Balance = 17
		--and i.MesFinal1 <> MesFinal2
		and i.CodigoConcepto IN(18,4,52,53,54)
) a		left join [InformesComiteDB].dbo.InformesPresentaciones		p	on a.CodigoPresentacion = p.codigopresentacion
		left join [InformesComiteDB].dbo.vw_InformesSedesCentros	s	on	(case when a.CodigoPresentacion in (1,6,7,8,9,12,28,87,88) then 1 else 6 end) = s.empresa
																			and a.CodigoPresentacion = s.CodigoPresentacion
																			and rtrim(ltrim(a.sede)) = rtrim(ltrim(s.NombreSede))
																			and s.tipo in ('Colision','Colisión')
																			and s.NombreSeccion not like '%mesa%'
where sede <> ' ' 
and valor <> 0
and NombreConcepto = 'Mano de Obra'
--and Año = 2021
--and mes=2
--and sede = 'Colisión Dai Mirolindo'
--and (sede like '%ford%' or sede like '%FR-%')
--and sede like '%68%'
--order by sede
--and a.CodigoPresentacion = 12

--select * from [InformesComiteDB].[dbo].[vw_InformesSedesCentros] where NombrePresentacion like '%FORD%'

```