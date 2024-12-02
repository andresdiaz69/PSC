# Table: Requisiciones_Entrevista_Temp

| Column Name | Data Type | Nullable |
|-------------|-----------|----------|
| IdSolicitud | int | NO |
| FechaModificacion | datetime | YES |
| UserModifico | nvarchar | NO |
| CedulaCandidato | nvarchar | NO |
| IdEstadoCandidato | int | NO |
| IdEstadoReclutadorCandidato | smallint | YES |
| Telefono | nvarchar | YES |
| Celular | nvarchar | NO |
| Correo | nvarchar | NO |
| FechaNacimiento | datetime | YES |
| TipIdentificacion | char | YES |
| OrdenSeleccionCandidato | smallint | YES |
| ObservacionesCandidato | nvarchar | YES |
| CodTipoCalle | nvarchar | NO |
| NombreCalle | nvarchar | NO |
| NumCalle | nvarchar | NO |
| Piso | nvarchar | YES |
| Bloque | nvarchar | YES |
| Puerta | nvarchar | YES |
| Complemento | nvarchar | YES |
| DireccionCompleta | nvarchar | NO |
| RelacionesPersonales | bit | NO |
| Familiar_Activos | bit | YES |
| Parentesco_Familiar | nvarchar | YES |
| UserName_Familiar | bigint | YES |
| Nombre_Familiar | nvarchar | YES |
| CodEmpresa_Familiar | smallint | YES |
| Empresa_Familiar | nvarchar | YES |
| CodLinea_Familiar | smallint | YES |
| Linea_Familiar | nvarchar | YES |
| CodCargo_Familiar | smallint | YES |
| Cargo_Familiar | nvarchar | YES |
| TrabajoAnteriormente | bit | YES |
| CodCargoAnterior | smallint | YES |
| NombreCargoAnterior | nvarchar | YES |
| CodLineaAnterior | smallint | YES |
| NombreLineaAnterior | nvarchar | YES |
| FechaIngresoAnterior | datetime | YES |
| FechaRetiroAnterior | datetime | YES |
| CausaRetiro | nvarchar | YES |
| AnoRetiro | smallint | YES |
| FechaRegistro | datetime | YES |
| IdDocumento | smallint | NO |
| Archivo | nvarchar | NO |
| Seleccionado | smallint | NO |
| ObservacionesDocumentos | nvarchar | NO |
| FechaCreacion | datetime | YES |
| IdEstadoReclutador | smallint | NO |
| CodMunicipio | smallint | YES |
| Municipio | nvarchar | YES |
| CodCiudad | bigint | YES |
| Ciudad | nvarchar | YES |
| FechaPreEntrevista | datetime | YES |
| FechaEntrevista | datetime | YES |
| Edad | nvarchar | YES |
| Sexo | nvarchar | YES |
| EstadoCivil | nvarchar | YES |
| TipoVivienda | nvarchar | YES |
| CodCiudadCandidato | bigint | YES |
| CiudadCandidato | nvarchar | YES |
| BarrioCandidato | nvarchar | YES |
| NucleoFamiliar | nvarchar | YES |
| TieneProcesoActivo | bit | YES |
| CandidatoProcesoActivo | nvarchar | YES |
| Primaria | bit | YES |
| Bachillerato | bit | YES |
| Tecnico | bit | YES |
| Tecnologo | bit | YES |
| Profesional | bit | YES |
| Postgrado | bit | YES |
| CuentaConCertificado | bit | YES |
| FortalezasCargo | nvarchar | YES |
| HabilidadesCargo | nvarchar | YES |
| ComentariosAdicionales | nvarchar | YES |
| Recomendaciones | nvarchar | YES |
| ObservacionesEntrevista | nvarchar | YES |
| PrimerEmpleo | bit | NO |
| CabezaFamilia | bit | NO |
| IdRazonRechazoCandidato | smallint | YES |
