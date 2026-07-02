# Ceache Data Intake Kit v0.1

Este kit ayuda a recibir contexto y datos operativos de forma segura.

Sirve para personas, comunidades, acopios, voluntarios, transportistas, organizaciones y equipos tecnicos que quieran aportar informacion sin exponer datos personales.

## Objetivo

Convertir relatos, listas, hojas, formularios, apps o APIs en evidencia util para coordinar mejor.

La regla central es:

```text
Interoperar funciones, no personas.
```

## Que incluye

- `questions-by-actor.md`: preguntas para cada perfil.
- `intake_schema.csv`: campos minimos para recibir una contribucion.
- `field_mapping_template.csv`: plantilla para mapear columnas de una hoja/app al schema comun.
- `google_sheet_template.csv`: plantilla base para copiar en Google Sheet, Excel o CSV.
- `sample_safe_submission.csv`: ejemplo seguro, sin datos personales.
- `review_workflow.md`: estados de revision y criterios de bloqueo.
- `data-quality-checklist.md`: lista de verificacion antes de compartir datos.
- `API_CONTRACT_MINIMO.md`: contrato minimo para conectar apps o sistemas.

## Para gente normal

Puedes ayudar contando:

- que estas viendo;
- que se necesita;
- que se ofrece;
- donde, a nivel de zona general;
- desde cuando ocurre;
- que tan urgente es;
- si tienes una lista, hoja, app o contacto institucional.

No compartas nombres, cedulas, telefonos privados, direcciones exactas, salud individual, menores, personas desaparecidas ni chats privados.

## Para equipos tecnicos

Usa `intake_schema.csv` para recibir submissions y `field_mapping_template.csv` para mapear fuentes externas.

Si vas a empezar desde cero, usa `google_sheet_template.csv`.

Si ya tienes una app o API, usa `API_CONTRACT_MINIMO.md`.

Cada aporte debe tener:

- tipo de actor;
- zona agregada;
- tipo de necesidad u oferta;
- estado;
- fecha observada;
- fuente;
- permiso de uso;
- riesgo PII declarado;
- estado de revision.

## Estados

```text
received
needs_review
needs_cleaning
usable
blocked_pii
archived
```

Nada debe publicarse automaticamente.
