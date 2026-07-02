# Contrato de schemas v0.1.0

Author: Johaina Chavez
Agency: Ceache Lab
Document Status: Draft Contract
Date: 2026-07-02

## Proposito

Definir la capa comun minima que todos los schemas funcionales deben compartir antes de publicar datasets normalizados o conectar fuentes de forma recurrente.

Este contrato no habilita interoperabilidad automatica. Habilita un piloto controlado con revision humana.

## Principio

```text
Intake + catalogo + mapeo + validacion + decision humana.
```

No hay publicacion automatica.

No hay matching nominal.

No hay base maestra de personas.

## Campos transversales obligatorios

| Campo | Funcion |
| --- | --- |
| `source_id` | Identifica la fuente original. |
| `intake_id` | Identifica el envio o registro de recepcion. |
| `original_record_id` | Conserva trazabilidad al registro original cuando sea seguro. |
| `schema_version` | Version del schema usado para normalizar. |
| `vocabulary_version` | Version de vocabularios controlados. |
| `function_type` | Funcion normalizada: acopio, donacion, necesidad, refugio, voluntariado, entrega. |
| `permission_status` | Estado de permiso: publicable, interno, agregado, pendiente, no publicable. |
| `publication_allowed` | Indica si el registro puede publicarse despues de revision. |
| `geographic_granularity` | Nivel geografico: pais, estado, municipio, ciudad, zona, celda. |
| `location_precision` | Precision: exacta, aproximada, agregada, protegida, desconocida. |
| `aggregation_level` | Nivel de agregacion: registro operativo, lote, zona, grupo, conteo. |
| `small_group_risk` | Riesgo de reidentificacion por grupo pequeno. |
| `record_status` | Estado del registro: activo, historico, expirado, reemplazado, eliminado. |
| `valid_from` | Inicio de validez temporal. |
| `valid_to` | Fin de validez temporal, si aplica. |
| `verification_status` | Declarado, verificado, no verificado, contradictorio, desconocido. |
| `confidence_method` | Metodo usado para asignar confianza. |
| `normalization_method` | Como se transformo el dato para hacerlo comparable. |

## Reglas de bloqueo

Bloquear carga o publicacion si:

- contiene nombres, cedulas, telefonos privados, direcciones exactas, salud individual, menores, desaparecidos, fotos identificables o chats privados;
- la fuente declara riesgo PII alto o desconocido y no puede entregar version agregada;
- la licencia o permiso esta pendiente o es ambiguo;
- contiene ubicacion exacta de refugios, hogares, rutas sensibles, salud o entregas vulnerables;
- la combinacion de zona, fecha, categoria, cantidad, fuente y estado puede identificar grupos pequenos;
- contiene evidencia visual o texto libre sin revision humana.

## Formato v0 recomendado

La puerta de entrada debe ser formulario web.

CSV, XLSX, Google Sheet y API son formatos de intercambio, no puertas de publicacion.

La API se registra primero como metadato y documentacion. La conexion recurrente solo se evalua despues del piloto manual.

