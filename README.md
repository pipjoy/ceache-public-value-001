# Ceache Public Value Package 001

**Research Observation 001**  
Johaina Chavez, Data Scientist  
Ceache Lab  
Fecha: 2026-07-02

Este repositorio acompana una observacion de investigacion basada en evidencia local organizada.

La idea central es:

> La proliferacion de herramientas no implica necesariamente mayor coordinacion.

No es un ranking de apps. No es una base central de personas. No reemplaza proyectos existentes.

El cuerpo principal formula el fenomeno. Los archivos tecnicos quedan como anexo para auditoria, reproduccion y trabajo de datos.

## Para cualquier persona

Durante una emergencia aparecen aplicaciones, formularios, mapas, hojas de calculo, bots, directorios, repositorios y grupos de WhatsApp.

Eso puede parecer desorden. Pero tambien muestra algo importante: muchas personas estan intentando resolver partes distintas de un mismo sistema.

La observacion ayuda a preguntar:

- Por que muchas herramientas no necesariamente producen coordinacion?
- Que relaciones entre herramientas son observables?
- Que duplicaciones son utiles y cuales confunden?
- Que riesgos aparecen cuando las funciones tocan datos sensibles?
- La interoperabilidad explica mejor la coordinacion que el numero de aplicaciones?

## Para equipos tecnicos

Este repositorio contiene:

- una lectura publica del ecosistema digital;
- una tabla descargable por funcion y fuente;
- una matriz de cobertura funcional;
- una matriz plataforma-funcion;
- schemas CSV para datos operativos seguros;
- una capa comun de coordinacion;
- una guia de datos minimos;
- un kit de intake para recibir contexto sin publicar datos sensibles automaticamente;
- reglas de seguridad, licencia y atribucion.

La regla metodologica central es:

```text
Interoperar funciones, no personas.
```

La llave recomendada para comparar sistemas es:

```text
function + geography + time
```

La llave prohibida es:

```text
nombre + cedula + telefono + direccion exacta
```

## Evidencia base

Esta version parte de evidencia local ya organizada:

- 168 fuentes, proyectos o plataformas en `atlas/platform_function_matrix.csv`.
- 584 relaciones funcion-fuente en `atlas/ecosystem_function_public_table_2026-07-02.csv`.
- 43 repositorios analizados desde inventario tecnico local.
- 23 grupos o canales funcionales de coordinacion inventariados.
- un sistema longitudinal de observacion diaria.

## Entregables principales

```text
docs/
  001-mapa-del-ecosistema-digital.md
  common-coordination-layer-v0.1.md
  minimum-data-matrix.md
  quick-start-compartir-datos.md
  schema-contract-v0.1.0.md
  data-intake-tool-v0.md

atlas/
  ecosystem_function_public_table_2026-07-02.csv
  ecosystem_function_coverage_2026-07-02.csv
  platform_function_matrix.csv

schemas/
  common_coordination_item_schema.csv
  common_operational_signal_schema.csv
  acopios_schema.csv
  donaciones_schema.csv
  necesidades_schema.csv
  refugios_schema.csv
  voluntarios_schema.csv
  entregas_schema.csv
  source_catalog_schema.csv

intake-kit/
  README.md
  questions-by-actor.md
  intake_schema.csv
  field_mapping_template.csv
  google_sheet_template.csv
  sample_safe_submission.csv
  review_workflow.md
  data-quality-checklist.md
  API_CONTRACT_MINIMO.md
```

## Como usarlo

Si quieres entender el resultado:

1. Lee `docs/001-mapa-del-ecosistema-digital.md`.
2. Abre `atlas/ecosystem_function_coverage_2026-07-02.csv`.
3. Revisa `atlas/ecosystem_function_public_table_2026-07-02.csv`.

Si tienes una app, Excel, formulario o API:

1. Busca si tu funcion aparece en la tabla publica.
2. Revisa `docs/minimum-data-matrix.md`.
3. Compara tus campos con `schemas/`.
4. Lee `DATA_SAFETY.md`.
5. Usa `intake-kit/field_mapping_template.csv` para mapear tu estructura.
6. No envies datos personales, ubicaciones sensibles ni casos nominales.

## Que datos si se pueden compartir

- tipo de necesidad;
- categoria de recurso;
- zona agregada;
- estado operativo;
- fecha de actualizacion;
- fuente;
- canal institucional;
- nivel de verificacion;
- permiso o licencia;
- responsable institucional o tecnico.

## Que datos no se deben enviar ni publicar

Este repositorio no contiene y no solicita:

- nombres de personas vulnerables;
- cedulas o documentos;
- telefonos privados;
- direcciones exactas;
- ubicaciones sensibles;
- datos de menores;
- salud individual;
- listas nominales de refugios;
- reportes nominales de desaparecidos;
- fotos identificables;
- chats privados.

## Que trabajo hicimos

1. Reordenamos la evidencia desde funciones, no desde marcas.
2. Separamos herramientas existentes de vacios reales.
3. Creamos una tabla funcion-fuente descargable.
4. Marcamos riesgos PII por funcion.
5. Documentamos limites: lo que sabemos, lo que creemos y lo que todavia no sabemos.
6. Dejamos schemas y datos minimos como anexo tecnico, no como argumento central.

## Estado

Version: `v0.1.4`  
Estado: public value package, evidencia preliminar  
Licencia: ver `LICENSE.md`  
Contacto: ceachelab@gmail.com
