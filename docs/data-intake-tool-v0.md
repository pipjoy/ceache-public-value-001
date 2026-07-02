# Herramienta minima de recepcion segura de datos v0.1

Author: Johaina Chavez
Agency: Ceache Lab
Document Status: Tool Design
Date: 2026-07-02

## Objetivo

Disenar una herramienta minima para recibir datos operativos seguros desde organizaciones, apps, hojas de calculo o APIs, sin convertir la recepcion de datos en una base maestra de personas.

La version 0.1 debe permitir registrar una fuente, recibir una muestra o conexion de datos, evaluar permisos y riesgo PII, previsualizar campos, validar contra esquemas minimos y dejar trazabilidad suficiente para decidir si los datos pueden transformarse en un dataset publico normalizado.

## Principio de seguridad

La herramienta debe asumir que algunos datos llegan con mas riesgo del que la fuente cree. Por eso el flujo no publica, mezcla ni normaliza automaticamente ningun dato recibido.

Reglas base:

1. No pedir cedulas, nombres de personas vulnerables, telefonos privados, direcciones exactas sensibles, datos medicos individuales ni ubicaciones de refugios vulnerables.
2. Aceptar primero datos operativos agregados, institucionales y trazables.
3. Separar recepcion, validacion, revision humana y publicacion.
4. Registrar permisos y contacto institucional antes de procesar.
5. Bloquear la normalizacion publica si hay riesgo PII alto, licencia dudosa o fuente no verificable.

## Usuarios previstos

- Organizacion que tiene una hoja de calculo de acopios, refugios, necesidades, donaciones, voluntariado o entregas.
- Equipo tecnico que mantiene una app, mapa, formulario, bot o API.
- Institucion que puede compartir datos agregados bajo permiso.
- Voluntario autorizado que ayuda a preparar un archivo seguro en nombre de una organizacion.

## Alcance v0.1

La herramienta v0.1 debe funcionar como intake, catalogo, mapeo, validacion y decision humana. No debe funcionar como ingesta automatica ni como publicador directo.

Debe aceptar cuatro modos de entrada:

1. Formulario de fuente, para registrar metadatos sin cargar datos todavia.
2. Carga de archivo CSV o XLSX.
3. URL de Google Sheet.
4. URL de API.

Debe capturar siempre:

- tipo de dato;
- licencia o permiso;
- contacto institucional;
- declaracion de riesgo PII;
- fuente u organizacion responsable;
- metodo de actualizacion;
- restricciones de publicacion.

No debe incluir todavia:

- ingesta automatica recurrente sin revision;
- conexion automatica de API sin revision humana;
- deduplicacion entre fuentes;
- publicacion automatica;
- matching por personas;
- enriquecimiento con datos sensibles externos;
- sistema completo de permisos multirol, salvo autenticacion basica si se implementa dentro de una app existente.

Antes de recibir archivos, la fuente debe confirmar que no esta subiendo datos personales ni archivos originales con PII. Si no puede confirmarlo, solo se registran metadatos de la fuente.

## Tipos de dato iniciales

La seleccion minima debe incluir:

```text
acopio
refugio
necesidad
donacion
voluntariado
entrega_logistica
salud_agregada
conectividad
danos
informacion_verificada
otro
```

Para v0.1, los tipos prioritarios son:

1. acopio;
2. necesidad;
3. donacion;
4. refugio;
5. entrega_logistica;
6. voluntariado.

## Flujo recomendado

### Paso 1 - Registro de fuente

Campos:

```text
source_name
source_type
organization_name
organization_country
organization_scope
institutional_contact_name
institutional_contact_role
institutional_contact_email
institutional_contact_phone_optional
public_website_optional
source_description
data_owner_confirmation
```

Valores sugeridos para `source_type`:

```text
organization
app
google_sheet
spreadsheet
api
map
form
bot
repository
other
```

### Paso 2 - Metodo de entrega

El usuario elige una opcion:

```text
metadata_only
csv_upload
xlsx_upload
google_sheet_url
api_url
```

Campos por metodo:

CSV/XLSX:

```text
uploaded_file
file_original_name
file_size
file_hash
sheet_name_optional
header_row
```

Google Sheet:

```text
google_sheet_url
sheet_tab_name_optional
access_level_declared
refresh_expectation
```

API:

```text
api_url
api_method
api_auth_type
api_documentation_url_optional
sample_response_optional
refresh_expectation
rate_limit_notes_optional
```

Para v0.1, si una API requiere token privado, la herramienta debe recibir solo metadatos y coordinar acceso fuera del formulario hasta tener manejo seguro de secretos.

### Paso 3 - Tipo de dato y cobertura

Campos:

```text
data_type
data_subtype_optional
country
state_or_region_optional
municipality_optional
geographic_granularity
time_coverage_start_optional
time_coverage_end_optional
update_frequency
records_estimated
language
```

Valores para `geographic_granularity`:

```text
country
state
municipality
city
zone
approximate_point
exact_point
mixed
unknown
```

Si el usuario elige `exact_point`, la herramienta debe mostrar una advertencia de riesgo y pedir confirmar si la ubicacion exacta es publicable.

### Paso 4 - Licencia y permiso

Campos:

```text
permission_status
license_type
permission_statement
attribution_required
publication_allowed
derivatives_allowed
contact_for_permission
expiration_or_review_date_optional
```

Valores para `permission_status`:

```text
owner_authorized
public_data
authorized_by_partner
permission_pending
unknown
```

Valores para `publication_allowed`:

```text
yes_public
yes_aggregated_only
yes_after_review
internal_analysis_only
no
unknown
```

Regla: si `permission_status` es `permission_pending` o `unknown`, no se genera dataset publico.

### Paso 5 - Declaracion de riesgo PII

La fuente debe responder si los datos contienen o podrian contener:

```text
personal_names
personal_phone_numbers
personal_emails
national_ids
exact_home_addresses
health_individual_data
children_or_minors
missing_persons
survivor_or_victim_details
precise_sensitive_locations
small_group_identifiability
free_text_with_possible_pii
photos_or_media_with_people
```

Campos:

```text
pii_declared
pii_categories
pii_risk_level_declared
has_free_text_fields
sensitive_location_risk
small_group_risk
mitigation_proposed_by_source
review_requested
```

Valores para `pii_risk_level_declared`:

```text
none
low
medium
high
unknown
```

Reglas automaticas:

- si hay `national_ids`, `children_or_minors`, `missing_persons`, `health_individual_data` o `survivor_or_victim_details`, marcar riesgo alto;
- si hay texto libre, marcar para revision humana;
- si hay ubicaciones exactas de refugios, grupos pequenos o hogares, bloquear publicacion hasta agregacion;
- si `pii_risk_level_declared` es `unknown`, tratar como minimo riesgo medio.

### Paso 6 - Vista previa de campos

Para CSV, XLSX y Google Sheet accesible, la herramienta debe mostrar:

```text
column_name
sample_values_limited
inferred_type
empty_rate
possible_pii_flag
suggested_schema_field
required_field_match
```

Para API, la herramienta debe mostrar una muestra de claves JSON si el endpoint es publico o si se cargo una respuesta de ejemplo.

La vista previa no debe mostrar mas de 5 valores por columna y debe enmascarar valores que parezcan telefono, email, documento, coordenada exacta o direccion personal.

### Paso 7 - Mapeo de esquema

El usuario o revisor debe mapear columnas de origen a campos minimos.

Entidades iniciales:

```text
source_catalog
data_intake_log
schema_mapping
validation_report
pii_risk_report
normalized_public_dataset_candidate
```

El mapeo debe guardar:

```text
source_field
target_field
target_data_type
required
transformation_notes
confidence
review_status
```

### Paso 8 - Validacion y decision

Estados de una entrega:

```text
draft
submitted
needs_source_clarification
permission_review
pii_review
schema_review
accepted_for_internal_analysis
accepted_for_public_normalization
rejected_or_out_of_scope
archived
```

La herramienta debe generar una decision inicial:

```text
can_use_for_internal_analysis
can_publish_after_aggregation
can_publish_as_public_dataset
cannot_use_without_changes
```

La decision final debe quedar en manos de revision humana.

## Validaciones minimas

Validaciones de seguridad:

- licencia o permiso no vacio;
- contacto institucional obligatorio;
- declaracion PII obligatoria;
- bloqueo si hay PII alto no mitigado;
- advertencia si hay texto libre;
- advertencia si hay ubicacion exacta;
- advertencia si hay grupos pequenos identificables.

Validaciones de estructura:

- archivo CSV/XLSX legible;
- encabezados detectables;
- filas no vacias;
- tipo de dato seleccionado;
- fecha de actualizacion o cobertura temporal cuando exista;
- fuente y URL de fuente cuando aplique;
- mapeo minimo de campos requeridos por tipo de dato.

Validaciones de calidad:

- porcentaje de campos vacios;
- duplicados exactos;
- fechas imposibles;
- coordenadas fuera de rango;
- categorias no reconocidas;
- estados operativos fuera de vocabulario;
- unidades ambiguas.

## Modelo de datos minimo

### source_catalog

```text
source_id
source_name
source_type
organization_name
institutional_contact_name
institutional_contact_role
institutional_contact_email
public_website
permission_status
license_type
publication_allowed
data_types
geographic_scope
created_at
updated_at
review_status
```

### data_intake_log

```text
intake_id
source_id
delivery_method
data_type
file_hash_or_url
records_estimated
submitted_at
submitted_by
pii_risk_level_declared
pii_risk_level_computed
permission_status
validation_status
decision_status
reviewer_notes
```

### schema_mapping

```text
mapping_id
intake_id
source_field
target_field
target_entity
required
transformation_notes
confidence
review_status
created_at
```

### validation_report

```text
validation_report_id
intake_id
schema_version
required_fields_present
missing_required_fields
row_count
column_count
empty_field_summary
date_issues
geo_issues
category_issues
duplicate_issues
validation_result
created_at
```

### pii_risk_report

```text
pii_report_id
intake_id
declared_categories
computed_flags
free_text_fields
exact_location_fields
small_group_flags
recommended_action
risk_level
review_required
created_at
```

## Interfaz minima

Pantallas v0.1:

1. Nueva fuente.
2. Metodo de entrega.
3. Tipo de dato, cobertura y actualizacion.
4. Licencia y permisos.
5. Riesgo PII.
6. Vista previa y mapeo.
7. Resultado de validacion.
8. Confirmacion de recepcion.

La experiencia debe estar escrita para organizaciones no tecnicas. La herramienta debe permitir completar solo el formulario de fuente aunque todavia no tengan archivo listo.

Microcopy recomendado:

```text
No subas datos personales. Si tu archivo contiene nombres, telefonos, cedulas, direcciones exactas, datos de salud individual o informacion de menores, marca riesgo PII y comparte primero una version agregada.
```

```text
Ceache Lab revisara permisos, estructura y riesgo antes de usar o publicar cualquier dato.
```

## Salidas

La herramienta debe producir:

- `source_catalog`;
- `data_intake_log`;
- `schema_mapping`;
- `validation_report`;
- `pii_risk_report`;
- `normalized_public_dataset_candidate`, solo si pasa controles;
- registro de decision humana.

La version publica normalizada solo debe generarse si:

1. el permiso permite publicacion;
2. no hay PII alto sin mitigacion;
3. los campos minimos estan presentes o pueden mapearse;
4. la fuente es trazable;
5. la revision humana aprueba.

## Donde implementarlo si se decide construir

El repo principal es mayormente documental y de scripts Python. La app frontend adecuada es:

```text
external/build4venezuela
```

Es una app Next.js con App Router, Supabase, Clerk, Zod, componentes UI y rutas de formulario ya existentes para proyectos y solicitudes. La ruta candidata seria:

```text
external/build4venezuela/src/app/[locale]/(project-routes)/data-intake
```

APIs candidatas:

```text
external/build4venezuela/src/app/api/data-intake/sources/route.ts
external/build4venezuela/src/app/api/data-intake/submissions/route.ts
external/build4venezuela/src/app/api/data-intake/submissions/[intakeId]/route.ts
```

Librerias o carpetas candidatas:

```text
external/build4venezuela/src/lib/data-intake/schema.ts
external/build4venezuela/src/lib/data-intake/store.ts
external/build4venezuela/src/lib/data-intake/validation.ts
external/build4venezuela/src/lib/data-intake/pii.ts
```

La implementacion deberia reutilizar Zod para validar formularios, Supabase para persistencia, Clerk si se exige autenticacion, y el patron existente de `src/lib/requests` o `src/lib/projects` para stores, queries y rutas API.

No se recomienda construir todavia hasta revisar:

- modelo de autenticacion deseado para organizaciones externas;
- manejo seguro de archivos;
- almacenamiento de archivos y retencion;
- si Supabase debe guardar archivos o solo metadatos;
- politica de secretos para APIs privadas;
- vocabularios minimos por tipo de dato.

## Version 0.1 recomendada

La version 0.1 mas segura y util debe ser:

1. formulario web de fuente;
2. carga CSV/XLSX con previsualizacion limitada;
3. registro de URL de Google Sheet;
4. registro de URL de API;
5. declaracion obligatoria de licencia/permiso;
6. contacto institucional obligatorio;
7. declaracion PII obligatoria;
8. mapeo manual de columnas;
9. validacion automatica basica;
10. decision humana antes de normalizar o publicar.

Esta version permite recibir datos de manera ordenada sin prometer interoperabilidad automatica antes de tener seguridad, permisos y esquemas estables.
