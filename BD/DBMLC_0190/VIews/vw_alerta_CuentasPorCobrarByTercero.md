# View: vw_alerta_CuentasPorCobrarByTercero

## Usa los objetos:
- [[Empresas]]
- [[vw_alerta_CuentasPorCobrar]]

```sql





CREATE VIEW [dbo].[vw_alerta_CuentasPorCobrarByTercero]
AS
SELECT        

vw_alerta_CuentasPorCobrar.Ano_Periodo, 
vw_alerta_CuentasPorCobrar.Mes_Periodo, 
vw_alerta_CuentasPorCobrar.IdEmpresas, 
dbo.Empresas.NombreEmpresa AS Empresa, 
dbo.Empresas.SiglaEmpresa, 
IDSpiga, 
MAX(Tercero) AS Tercero, 
SUM(Valor) AS Valor

FROM            vw_alerta_CuentasPorCobrar INNER JOIN
                         dbo.Empresas ON vw_alerta_CuentasPorCobrar.IdEmpresas = dbo.Empresas.CodigoEmpresa

GROUP BY 
vw_alerta_CuentasPorCobrar.Ano_Periodo, 
vw_alerta_CuentasPorCobrar.Mes_Periodo, 
vw_alerta_CuentasPorCobrar.IdEmpresas, 
vw_alerta_CuentasPorCobrar.IDSpiga, 
dbo.Empresas.NombreEmpresa, 
dbo.Empresas.SiglaEmpresa


```