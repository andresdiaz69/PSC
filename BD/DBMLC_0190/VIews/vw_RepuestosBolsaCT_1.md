# View: vw_RepuestosBolsaCT_1

## Usa los objetos:
- [[Centros]]
- [[ComisionesSpigaAlmacenAlbaran]]
- [[Secciones]]
- [[Sedes]]
- [[vw_PorcentajeRecaudoAlmacenFactura]]

```sql







CREATE VIEW [dbo].[vw_RepuestosBolsaCT_1]
AS
SELECT        dbo.vw_PorcentajeRecaudoAlmacenFactura.Ano_Periodo, dbo.vw_PorcentajeRecaudoAlmacenFactura.Mes_Periodo, dbo.vw_PorcentajeRecaudoAlmacenFactura.CodigoEmpresa, dbo.Sedes.CodigoSede, 
                         dbo.Sedes.NombreSede, dbo.Centros.CodigoCentro, dbo.Centros.NombreCentro, dbo.Secciones.CodigoSeccion, dbo.Secciones.Seccion, dbo.Sedes.BolsaPorcentaje, dbo.Sedes.BolsaPuntos, 
                         dbo.vw_PorcentajeRecaudoAlmacenFactura.NumeroFactura, dbo.vw_PorcentajeRecaudoAlmacenFactura.TotalFactura, dbo.vw_PorcentajeRecaudoAlmacenFactura.ImporteEfecto, 
                         dbo.vw_PorcentajeRecaudoAlmacenFactura.PorcentajeRecaudo, 
                         SUM(dbo.ComisionesSpigaAlmacenAlbaran.UnidadesVendidas * dbo.ComisionesSpigaAlmacenAlbaran.ValorUnitarioReferencia - dbo.ComisionesSpigaAlmacenAlbaran.UnidadesVendidas * dbo.ComisionesSpigaAlmacenAlbaran.ValorUnitarioReferencia
                          * dbo.ComisionesSpigaAlmacenAlbaran.PorcDescuento / 100) AS ValorBaseMostrador, 
                         SUM((dbo.ComisionesSpigaAlmacenAlbaran.UnidadesVendidas * dbo.ComisionesSpigaAlmacenAlbaran.ValorUnitarioReferencia - dbo.ComisionesSpigaAlmacenAlbaran.UnidadesVendidas * dbo.ComisionesSpigaAlmacenAlbaran.ValorUnitarioReferencia
                          * dbo.ComisionesSpigaAlmacenAlbaran.PorcDescuento / 100) * (dbo.vw_PorcentajeRecaudoAlmacenFactura.PorcentajeRecaudo / 100)) AS ValorNetoMostrador
FROM            dbo.Secciones RIGHT OUTER JOIN
                         dbo.vw_PorcentajeRecaudoAlmacenFactura ON dbo.Secciones.CodigoSeccion = dbo.vw_PorcentajeRecaudoAlmacenFactura.FkSecciones LEFT OUTER JOIN
                         dbo.ComisionesSpigaAlmacenAlbaran ON dbo.vw_PorcentajeRecaudoAlmacenFactura.NumeroFactura = dbo.ComisionesSpigaAlmacenAlbaran.NumeroFactura LEFT OUTER JOIN
                         dbo.Sedes INNER JOIN
                         dbo.Centros ON dbo.Sedes.CodigoSede = dbo.Centros.CodigoSede ON dbo.vw_PorcentajeRecaudoAlmacenFactura.CodigoCentro = dbo.Centros.CodigoCentro
WHERE        
(NOT (dbo.ComisionesSpigaAlmacenAlbaran.Seccion LIKE N'%insumos%'))
--AND (dbo.ComisionesSpigaAlmacenAlbaran.FechaFactura <= '20191031' OR dbo.ComisionesSpigaAlmacenAlbaran.CedulaVendedorRepuestos IN (1043875927, 79497419, 93380721, 406824, 11275377, 11313710, 16362509, 16594756, 16745552, 17342981, 26460616, 72231687, 72291293, 80053904, 94373171, 94491437, 1014201465, 1022322789, 1036661930, 1052391504, 1064985454, 1065599422, 1065825536, 1067912772, 1110486367, 1110517646, 1110553214, 1110583916, 1121860719, 1130665273, 1152206210))
AND (dbo.ComisionesSpigaAlmacenAlbaran.FechaFactura <= '20191031')

GROUP BY dbo.vw_PorcentajeRecaudoAlmacenFactura.Ano_Periodo, dbo.vw_PorcentajeRecaudoAlmacenFactura.Mes_Periodo, dbo.vw_PorcentajeRecaudoAlmacenFactura.CodigoEmpresa, 
                         dbo.vw_PorcentajeRecaudoAlmacenFactura.NumeroFactura, dbo.vw_PorcentajeRecaudoAlmacenFactura.TotalFactura, dbo.vw_PorcentajeRecaudoAlmacenFactura.ImporteEfecto, 
                         dbo.vw_PorcentajeRecaudoAlmacenFactura.PorcentajeRecaudo, dbo.Sedes.CodigoSede, dbo.Sedes.NombreSede, dbo.Sedes.BolsaPorcentaje, dbo.Sedes.BolsaPuntos, dbo.Centros.CodigoCentro, dbo.Centros.NombreCentro, 
                         dbo.Secciones.CodigoSeccion, dbo.Secciones.Seccion
HAVING        (dbo.vw_PorcentajeRecaudoAlmacenFactura.CodigoEmpresa <> 6)


```