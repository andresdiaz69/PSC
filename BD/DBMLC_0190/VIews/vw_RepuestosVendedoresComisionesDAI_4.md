# View: vw_RepuestosVendedoresComisionesDAI_4

## Usa los objetos:
- [[vw_RepuestosVendedoresComisionesDAI_2]]
- [[vw_RepuestosVendedoresComisionesDAI_3]]

```sql

CREATE VIEW [dbo].[vw_RepuestosVendedoresComisionesDAI_4]
AS
SELECT        ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.Ano_Periodo, dbo.vw_RepuestosVendedoresComisionesDAI_3.Ano_Periodo) AS Ano_Periodo, ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.Mes_Periodo, 
                         dbo.vw_RepuestosVendedoresComisionesDAI_3.Mes_Periodo) AS Mes_Periodo, ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.CodigoEmpresa, dbo.vw_RepuestosVendedoresComisionesDAI_3.CodigoEmpresa) 
                         AS CodigoEmpresa, ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.CedulaVendedorRepuestos, dbo.vw_RepuestosVendedoresComisionesDAI_3.CedulaVendedorRepuestos) AS CedulaVendedorRepuestos, 
                         ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.ValorVariable, dbo.vw_RepuestosVendedoresComisionesDAI_3.ValorVariable) AS ValorVariable, 
                         ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.ValorBaseMostrador, 0) AS ValorBaseMostrador, ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.ComisionMostrador, 0) AS ComisionMostrador, 
                         ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_3.ValorBaseTaller, 0) AS ValorBaseTaller, ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_3.ComisionTaller, 0) AS ComisionTaller, 
                         ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_2.ComisionMostrador, 0) + ISNULL(dbo.vw_RepuestosVendedoresComisionesDAI_3.ComisionTaller, 0) AS Comision
FROM            dbo.vw_RepuestosVendedoresComisionesDAI_2 FULL OUTER JOIN
                         dbo.vw_RepuestosVendedoresComisionesDAI_3 ON dbo.vw_RepuestosVendedoresComisionesDAI_2.Ano_Periodo = dbo.vw_RepuestosVendedoresComisionesDAI_3.Ano_Periodo AND 
                         dbo.vw_RepuestosVendedoresComisionesDAI_2.Mes_Periodo = dbo.vw_RepuestosVendedoresComisionesDAI_3.Mes_Periodo AND 
                         dbo.vw_RepuestosVendedoresComisionesDAI_2.CodigoEmpresa = dbo.vw_RepuestosVendedoresComisionesDAI_3.CodigoEmpresa AND 
                         dbo.vw_RepuestosVendedoresComisionesDAI_2.CedulaVendedorRepuestos = dbo.vw_RepuestosVendedoresComisionesDAI_3.CedulaVendedorRepuestos





```