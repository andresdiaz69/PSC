# View: vw_JefesDeTallerVolkswagen_3

## Usa los objetos:
- [[vw_JefesDeTallerVolkswagen_3_Detalle]]

```sql







CREATE VIEW [dbo].[vw_JefesDeTallerVolkswagen_3]
AS
SELECT        Ano_Periodo, Mes_Periodo, CodigoEmpresa, CodigoCentro, Centro, CodigoSeccion, Seccion, MAX(ValorVariable) AS ValorVariable, SUM(Facturacion) AS Facturacion, SUM(Facturacion) * MAX(ValorVariable) / 100 AS Comision_Facturacion
FROM            dbo.vw_JefesDeTallerVolkswagen_3_Detalle
GROUP BY Ano_Periodo, Mes_Periodo, CodigoEmpresa, CodigoCentro, Centro, CodigoSeccion, Seccion


```