# Matriz minima de datos compartibles

Author: Johaina Chavez
Agency: Ceache Lab
Document Status: Draft v0.1
Date: 2026-07-02

## Objetivo

Convertir el plan de interoperabilidad en esquemas concretos de datos minimos para que organizaciones, plataformas, hojas de calculo, mapas, formularios y APIs puedan compartir informacion operativa sin exponer personas.

La regla central es:

> Interoperar funciones, no personas.

Ceache Lab no necesita una base maestra de individuos. Necesita una capa minima, agregada, trazable y comparable para observar funciones de respuesta: acopios, donaciones, necesidades, refugios, voluntariado, entregas y fuentes.

## Regla de seguridad

Los esquemas minimos no incluyen ni deben recibir:

- cedulas;
- nombres de personas vulnerables;
- telefonos privados;
- ubicaciones exactas sensibles;
- salud individual;
- datos de menores;
- texto libre con informacion personal;
- fotos o evidencias identificables de personas afectadas.

Si una fuente contiene esos datos, debe producir una version agregada o filtrada antes de interoperar.

## Llaves recomendadas

Las conexiones entre sistemas deben usar:

```text
function + geography + time
```

Ejemplos:

- categoria de necesidad + zona_agregada + fecha_actualizacion;
- categoria de donacion + ubicacion_destino_agregada + estado;
- tipo de refugio + zona_agregada + estado_operativo;
- etapa de entrega + origen_agregado + destino_agregado + fecha_etapa.

Las conexiones no deben usar:

```text
nombre + cedula + telefono + direccion exacta
```

## Esquemas creados

Los esquemas CSV estan en `schemas/` y comparten estas columnas:

```text
field
type
required
description
example
pii_risk
public_allowed
```

| Funcion | Archivo | Proposito minimo | Unidad de interoperabilidad |
|---|---|---|---|
| Acopios | `schemas/acopios_schema.csv` | Publicar puntos o redes de recepcion y su estado operativo | punto o red de acopio |
| Donaciones | `schemas/donaciones_schema.csv` | Separar oferta, recepcion, clasificacion y asignacion de ayuda | lote agregado de donacion |
| Necesidades | `schemas/necesidades_schema.csv` | Comparar brechas reportadas por categoria, zona y tiempo | necesidad agregada |
| Refugios | `schemas/refugios_schema.csv` | Observar capacidad, ocupacion y necesidades sin exponer personas alojadas | refugio o codigo publico |
| Voluntarios | `schemas/voluntarios_schema.csv` | Coordinar capacidades humanas agregadas por habilidad y zona | pool agregado de voluntariado |
| Entregas | `schemas/entregas_schema.csv` | Seguir etapas logisticas sin publicar rutas vulnerables | movimiento o entrega agregada |
| Source catalog | `schemas/source_catalog_schema.csv` | Registrar fuentes, permisos, riesgos y mapeo de esquemas | fuente de datos |

## Campos transversales para contrato v0.1.0

Antes de publicar datasets normalizados, cada schema funcional debe alinearse con un contrato comun.

Campos transversales recomendados:

```text
source_id
intake_id
original_record_id
schema_version
vocabulary_version
function_type
permission_status
publication_allowed
geographic_granularity
location_precision
aggregation_level
small_group_risk
record_status
valid_from
valid_to
verification_status
confidence_method
normalization_method
```

Estos campos separan cuatro cosas que no deben mezclarse:

- origen del dato;
- permiso de uso;
- granularidad y riesgo;
- estado de verificacion/publicacion.

Los CSV actuales son suficientes para piloto controlado. No son todavia contrato final de interoperabilidad automatica.

## Campos por funcion

### Acopios

Campos minimos:

```text
acopio_id
nombre_publico
tipo
pais
estado
municipio
ciudad
zona_agregada
lat_lng_aproximado
estado_operativo
categorias_recibe
categorias_necesita
horario
contacto_institucional_publico
fuente
url_fuente
ultima_actualizacion
licencia
nivel_confianza
restricciones_publicacion
```

Uso: saber donde se puede recibir o buscar ayuda, detectar zonas sin cobertura visible y evitar duplicacion.

Control: la coordenada solo puede ser aproximada o segura; el contacto debe ser institucional, publico o enmascarado.

### Donaciones

Campos minimos:

```text
donacion_id
categoria
subcategoria
cantidad
unidad
estado
ubicacion_origen_agregada
ubicacion_destino_agregada
fecha_disponible
fecha_actualizacion
restricciones
organizacion_o_fuente
url_fuente
nivel_confianza
limitaciones
```

Uso: distinguir oferta de necesidad, detectar saturacion por categoria y orientar donaciones hacia brechas reales.

Estados recomendados: `ofrecida`, `recibida_en_centro`, `clasificada`, `asignada`, `en_camino`, `distribuida`, `no_utilizable`, `desconocida`.

### Necesidades

Campos minimos:

```text
necesidad_id
categoria
subcategoria
urgencia
estado
zona_agregada
cantidad_estimada
unidad
fecha_reporte
fecha_actualizacion
fuente
metodo
nivel_confianza
limitaciones
pii_risk
```

Uso: ver que cambia, priorizar, detectar necesidades persistentes o envejecidas y comparar necesidad visible con ayuda visible.

Estados recomendados: `reportada`, `verificada`, `en_atencion`, `cubierta`, `parcialmente_cubierta`, `expirada`, `desconocida`.

### Refugios

Campos minimos:

```text
refugio_id
nombre_publico_o_codigo
tipo
zona_agregada
estado_operativo
capacidad_total
ocupacion_estimada
servicios_disponibles
necesidades_actuales
acepta_voluntarios
fecha_actualizacion
fuente
nivel_confianza
restricciones_publicacion
```

Uso: estimar capacidad visible, identificar saturacion y conectar necesidades de agua, salud, higiene y alimentos.

Control: no publicar ubicacion exacta sensible, datos de personas alojadas ni grupos pequenos identificables.

### Voluntarios

Campos minimos:

```text
volunteer_pool_id
tipo_habilidad
cantidad_disponible
zona_agregada
disponibilidad
organizacion_coordinadora
estado
fecha_actualizacion
fuente
nivel_confianza
restricciones_publicacion
```

Uso: coordinar capacidades, conectar habilidades con necesidades y evitar exposicion individual.

Control: observar voluntariado como agregados; no nombres, documentos, telefonos privados, ubicaciones personales ni disponibilidad individual sensible.

### Entregas

Campos minimos:

```text
delivery_id
categoria
cantidad
unidad
origen_agregado
destino_agregado
etapa
fecha_etapa
actor_responsable
fuente
evidencia
nivel_confianza
limitaciones
```

Uso: separar promesa, stock, despacho, transito, llegada, distribucion y recepcion.

Etapas recomendadas: `prometida`, `en_stock`, `despachada`, `en_transito`, `llegada`, `distribuida`, `recibida`, `no_confirmada`.

Control: no publicar rutas vulnerables ni evidencia identificable.

### Source catalog

Campos minimos:

```text
source_id
source_name
source_type
function_covered
owner_type
geographic_scope
access_method
source_url
license
sharing_permission
update_frequency
last_checked_at
schema_mapping_status
has_pii_flag
pii_review_status
institutional_contact_channel
attribution
notes
```

Uso: registrar de donde viene cada dato, que permiso tiene, que funcion cubre, si contiene riesgo PII y si puede mapearse al esquema minimo.

Control: el contacto debe ser institucional o publico. Si una fuente tiene PII, no entra al dataset publico hasta tener version agregada y revision aprobada.

## Politica de publicacion

`public_allowed=true` significa que el campo puede publicarse si la fuente y licencia lo permiten.

`public_allowed=conditional` significa que el campo requiere revision humana, enmascaramiento, agregacion o eliminacion antes de publicarse.

`pii_risk=medium` no significa que el campo sea PII por si mismo. Significa que puede volverse sensible al combinarse con otros campos o al publicarse con demasiado detalle.

## Version minima operativa

Para pilotos, una fuente puede interoperar si provee al menos:

```text
id estable
funcion
categoria o tipo
zona_agregada
estado
fecha_actualizacion
fuente
nivel_confianza o metodo
licencia o permiso
```

Esto permite comparar sistemas sin convertir la coordinacion humanitaria en una base de datos de personas.
