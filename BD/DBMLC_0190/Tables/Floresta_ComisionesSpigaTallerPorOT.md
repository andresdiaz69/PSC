# Table: Floresta_ComisionesSpigaTallerPorOT

| Column Name | Data Type | Nullable |
|-------------|-----------|----------|
| Ano_Periodo | int | NO |
| Mes_Periodo | int | NO |
| CodigoEmpresa | smallint | NO |
| Empresa | nvarchar | NO |
| CodigoCentro | smallint | NO |
| Centro | nvarchar | NO |
| CodigoSeccion | int | NO |
| Seccion | nvarchar | NO |
| NumOT | nvarchar | YES |
| NumeroFacturaTaller | nvarchar | NO |
| NumeroAlbaran | nvarchar | YES |
| FechaAperturaOrden | datetime | NO |
| FechaFactura | datetime | YES |
| fechaentrega | datetime | YES |
| Placa | nvarchar | YES |
| VIN | nvarchar | YES |
| FkServicioTipos | tinyint | YES |
| Marcaveh | smallint | NO |
| NombreMarca | nvarchar | YES |
| Gama | smallint | NO |
| NombreGama | nvarchar | YES |
| NitCliente | nvarchar | YES |
| NombreCliente | nvarchar | YES |
| CodigoCategoriaCliente | smallint | YES |
| CategoriaCliente | nvarchar | YES |
| TipoCargo | nvarchar | NO |
| TipoIntCargo | nvarchar | NO |
| marca | nvarchar | YES |
| Codigo | nvarchar | YES |
| descripcion | nvarchar | YES |
| TipoOperacion | varchar | NO |
| ValorUnitario | decimal | NO |
| UnidadesVendidas | decimal | YES |
| PorcentajeDescuento | decimal | YES |
| ImporteImpuesto | decimal | YES |
| CedulaOperario | bigint | YES |
| NombreOperario | nvarchar | YES |
| CedulaAsesorServicioAlta | bigint | YES |
| AsesorServicioAlta | nvarchar | YES |
| CedulaAsesorServicioResponsable | bigint | YES |
| AsesorServicioResponsable | nvarchar | YES |
| CedulaAsesorServicioCierre | bigint | YES |
| AsesorServicioCierre | nvarchar | YES |
| CedulaAsesorServicioRetirada | bigint | YES |
| AsesorServicioRetirada | nvarchar | YES |
| TrabajoRetorno | bit | NO |
| Cotizacion | int | NO |
| CampañaRepuesto | int | YES |
| CodClas1 | nvarchar | YES |
| DescripClas1 | nvarchar | YES |
| CodClas2 | nvarchar | YES |
| DescripClas2 | nvarchar | YES |
| CodClas3 | nvarchar | YES |
| DescripClas3 | nvarchar | YES |
| CodClas4 | nvarchar | YES |
| DescripClas4 | nvarchar | YES |
| CodClas5 | nvarchar | YES |
| DescripClas5 | nvarchar | YES |
| CodClas6 | nvarchar | YES |
| DescripClas6 | nvarchar | YES |
| CedulaVendedorRepuestos | bigint | YES |
| NombreVendedorRepuestos | nvarchar | YES |
| CedulaBodeguero | bigint | YES |
| NombreBodeguero | nvarchar | YES |
| ValorNeto | decimal | YES |
| Coste | decimal | YES |
| IdImputaciontipos | smallint | YES |
| TipoImputacion | nvarchar | YES |
| DescripcionTrabajo | nvarchar | YES |
