# View: vw_RepuestosV2_VendedoresDeTienda_2

## Usa los objetos:
- [[vw_RepuestosV2_VendedoresDeTienda_1]]

```sql






CREATE VIEW [dbo].[vw_RepuestosV2_VendedoresDeTienda_2]
AS
SELECT        Ano_Periodo, Mes_Periodo, CodigoEmpresa, CedulaVendedorRepuestos, SUM(ValorBaseMostrador) AS ValorBaseMostrador
FROM            dbo.vw_RepuestosV2_VendedoresDeTienda_1
GROUP BY Ano_Periodo, Mes_Periodo, CodigoEmpresa, CedulaVendedorRepuestos







```