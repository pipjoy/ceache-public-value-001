# Review Workflow

Ningun aporte se publica automaticamente.

## Estados

### received

El aporte fue recibido, pero todavia no fue revisado.

### needs_review

Requiere lectura humana para detectar datos sensibles, ambiguedad o falta de permiso.

### needs_cleaning

Puede ser util, pero requiere normalizacion:

- categorias;
- zonas;
- fechas;
- unidades;
- estados;
- duplicados.

### usable

Puede usarse para analisis interno o publicacion agregada.

### blocked_pii

No puede usarse ni publicarse porque contiene o podria revelar datos sensibles.

### archived

Se conserva como registro interno no activo o se descarta segun politica de retencion.

## Criterios de bloqueo

Bloquear si contiene:

- nombres de personas vulnerables;
- cedulas;
- telefonos privados;
- direcciones exactas;
- salud individual;
- menores;
- personas desaparecidas;
- fotos identificables;
- chats privados;
- rutas sensibles.

## Criterios para usar

Un aporte puede usarse si:

- tiene zona agregada;
- tiene fecha aproximada;
- tiene categoria operativa;
- tiene permiso suficiente;
- no contiene PII;
- puede mapearse a un schema;
- no contradice reglas de seguridad.

