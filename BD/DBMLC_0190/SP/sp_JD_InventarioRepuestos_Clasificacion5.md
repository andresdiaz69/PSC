# Stored Procedure: sp_JD_InventarioRepuestos_Clasificacion5

## Usa los objetos:
- [[PrecioRepuestosJDAgricola]]
- [[PrecioRepuestosJDCania]]
- [[PrecioRepuestosJDConstruccion]]
- [[spiga_StockRepuestos]]
- [[UnidadDeNegocio]]

```sql

CREATE PROC [dbo].[sp_JD_InventarioRepuestos_Clasificacion5]
(
	@FechaConsulta DATE
)AS
BEGIN
	
	SET NOCOUNT ON
	SET FMTONLY OFF

	--DECLARE @FechaConsulta DATE
	--SET @FechaConsulta = '20210929'

	SELECT DISTINCT Ano_Periodo,Mes_Periodo,IdReferencias,IdClasificacion5,DenominacionClasificacion5,
		CASE WHEN IdClasificacion5 IN ('5','4') THEN 'JOH' ELSE IdMR END IdMR
	FROM 
	(
		SELECT Ano_Periodo,Mes_Periodo,IdEmpresas,NombreEmpresa,IdMarcas,NombreMarca,IdCentros,NombreCentro,IdSecciones,NombreSeccion,IdReferencias,
			CASE WHEN IdClasificacion6 in ('3','1','9') THEN '4'					
				WHEN IdClasificacion6 = '2' THEN '5'
				WHEN IdClasificacion5 NOT IN ('4','5','6','7','10') THEN NULL
				ELSE IdClasificacion5 END AS IdClasificacion5,
			CASE WHEN IdClasificacion6 in ('3','1','9') THEN 'AGRÍCOLA'
				WHEN IdClasificacion6 = '2' THEN 'CONSTRUCCIÓN'
				WHEN IdClasificacion5 NOT IN ('4','5','6','7','10') THEN NULL
				ELSE DenominacionClasificacion5 END AS DenominacionClasificacion5,IdClasificacion6,DenominacionClasificacion6,PrecioMedio,stock,
				IdMR
		FROM 
		(
			SELECT DISTINCT Ano_Periodo,Mes_Periodo,IdEmpresas,NombreEmpresa,IdMarcas,NombreMarca,IdCentros,NombreCentro,IdSecciones,NombreSeccion,IdReferencias,
				CASE WHEN RefAgr.Referencia IS NOT NULL OR RefCania.PartNumber IS NOT NULL THEN '4' 			
					WHEN RefContr.Referencia IS NOT NULL THEN '5'
					ELSE IdClasificacion5 END AS IdClasificacion5,
				CASE WHEN RefAgr.Referencia IS NOT NULL OR RefCania.PartNumber IS NOT NULL THEN 'AGRÍCOLA'
					WHEN RefContr.Referencia IS NOT NULL THEN 'CONSTRUCCIÓN'
					ELSE DenominacionClasificacion5 END AS DenominacionClasificacion5,
				CASE WHEN RefAgr.Referencia IS NOT NULL THEN '1'
					WHEN RefCania.PartNumber IS NOT NULL THEN '3'
					WHEN RefContr.Referencia IS NOT NULL THEN '2'
					ELSE IdClasificacion6 END AS IdClasificacion6,
				CASE WHEN RefAgr.Referencia IS NOT NULL	THEN 'Agricola'		
					WHEN RefCania.PartNumber IS NOT NULL THEN 'Caña'
					WHEN RefContr.Referencia IS NOT NULL THEN 'Construccion'
					ELSE DenominacionClasificacion6 END AS DenominacionClasificacion6, PrecioMedio,stock, IdMR
			FROM 
			(	
				SELECT Ano_Periodo, Mes_Periodo, IdEmpresas, NombreEmpresa, CONVERT(smallint,CodigoMarca)IdMarcas, NombreMarca, IdCentros, NombreCentro, IdSecciones, 
					NombreSeccion,IdReferencias, PrecioMedio,stock ,IdMR,
					CASE WHEN IdMR IN ('BEN','CIB','HAM','KLE','OTR','VOG','WIR') THEN '7' ELSE IdClasificacion5 END AS IdClasificacion5,
					CASE WHEN IdMR IN ('BEN','CIB','HAM','KLE','OTR','VOG','WIR') THEN 'WIRTGEN' ELSE DenominacionClasificacion5 END AS DenominacionClasificacion5,
					CASE WHEN IdMR IN ('BEN','CIB','HAM','KLE','OTR','VOG','WIR') THEN '5' ELSE IdClasificacion6 END AS IdClasificacion6,
					CASE WHEN IdMR IN ('BEN','CIB','HAM','KLE','OTR','VOG','WIR') THEN 'Wirtgen' ELSE DenominacionClasificacion6 END AS DenominacionClasificacion6
				FROM
				(
					SELECT i.Ano_Periodo,i.Mes_Periodo,i.IdEmpresas,CASE WHEN i.IdEmpresas=1 THEN 'CasaToro'  end NombreEmpresa,
						CASE WHEN  denominacionclasificacion6 like '%Merchandising%' THEN  411
								WHEN  denominacionclasificacion6 like '%Lubricantes%'THEN 410
								WHEN denominacionclasificacion5 LIKE '%CONSTRUCCI%' THEN 411
								WHEN denominacionclasificacion5 like '%WIRTGEN%' THEN 520
								WHEN denominacionclasificacion5 is null AND denominacionclasificacion6  is null AND nombreseccion like '%AGR%'THEN 410
								WHEN denominacionclasificacion5 is null AND denominacionclasificacion6 is null AND nombreseccion like '%CONS%'THEN 411
								WHEN denominacionclasificacion5 is null AND denominacionclasificacion6  is null AND nombreseccion like '%WIR%'THEN  520
								ELSE 410 END 'CodigoMarca',
						CASE WHEN  denominacionclasificacion6 like '%Merchandising%' THEN 'JD Construccion' 
								WHEN  denominacionclasificacion6 like '%Lubricantes%'THEN 'JD Agricola'
								WHEN denominacionclasificacion5 LIKE '%CONSTRUCCI%' THEN 'JD Construccion'
								WHEN denominacionclasificacion5 like '%WIRTGEN%' THEN 'JD Wirtgen'
								WHEN denominacionclasificacion5 is null AND denominacionclasificacion6  is null AND nombreseccion like '%AGR%'THEN 'JD Agricola'
								WHEN denominacionclasificacion5 is null AND denominacionclasificacion6 is null AND nombreseccion like '%CONS%'THEN 'JD Construccion'
								WHEN denominacionclasificacion5 is null AND denominacionclasificacion6  is null AND nombreseccion like '%WIR%'THEN 'JD Wirtgen'
								ELSE 'JD Agricola' END 'NombreMarca',
						i.IdCentros,n.nombrecentro,i.IdSecciones,n.nombreseccion,i.IdReferencias,i.IdClasificacion5,i.DenominacionClasificacion5,
						IdClasificacion6,i.DenominacionClasificacion6,I.PrecioMedio,I.stock,IdMR
					FROM [PSCService_DB].dbo.spiga_StockRepuestos i
					LEFT JOIN DBMLC_0190.dbo.UnidadDeNegocio n on i.IdEmpresas = n.CodEmpresa
					AND i.IdCentros = n.CodCentro
					AND i.IdSecciones = n.CodSeccion
					WHERE i.IdEmpresas = 1 AND i.IdCentros in (21,25,124,22,65,46,18,16,49,44,29,149,41,26)
						AND Ano_Periodo = YEAR(@FechaConsulta) AND Mes_Periodo = MONTH(@FechaConsulta) AND FechaDeCorte >= '20190101'
						AND (LTRIM(RTRIM(IdClasificacion5)) NOT IN ('4','5','7') OR IdClasificacion5 IS NULL)
				)A 
			)A
			LEFT JOIN 
			(
				SELECT * FROM PrecioRepuestosJDAgricola
				WHERE FechaRegistro = (SELECT FechaMaxima = MAX(FechaRegistro) FROM PrecioRepuestosJDAgricola WHERE FechaRegistro <= @FechaConsulta)
			) RefAgr on A.IdReferencias = RefAgr.Referencia

			LEFT JOIN 
			(
				SELECT * FROM PrecioRepuestosJDConstruccion
				WHERE FechaRegistro = (SELECT FechaMaxima = MAX(FechaRegistro) FROM PrecioRepuestosJDConstruccion WHERE FechaRegistro <= @FechaConsulta)
			) RefContr on A.IdReferencias = RefContr.Referencia

			LEFT JOIN 
			(
				SELECT * FROM PrecioRepuestosJDCania
				WHERE FechaRegistro = (SELECT FechaMaxima = MAX(FechaRegistro) FROM PrecioRepuestosJDCania WHERE FechaRegistro <= @FechaConsulta)
			) RefCania on A.IdReferencias = RefCania.PartNumber
		) B
	)A
	WHERE IdClasificacion5 IS NOT NULL

END

```