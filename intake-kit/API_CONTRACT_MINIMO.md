# API contract minimo para interoperabilidad segura

Johaina Chavez, Data Scientist  
Ceache Lab  
Version: 0.1.1  
Fecha: 2026-07-02

Este documento propone un contrato minimo para que apps, formularios, hojas o sistemas puedan compartir datos operativos sin exponer personas.

## Principio

```text
Interoperar funciones, no personas.
```

## Endpoint sugerido

```http
POST /api/v1/operational-signals
Content-Type: application/json
```

## Payload minimo

```json
{
  "record_id": "source-2026-07-02-001",
  "actor_type": "acopio",
  "data_type": "oferta",
  "category": "agua",
  "subcategory": "botellones",
  "description_safe": "Agua disponible para distribucion comunitaria",
  "quantity": 120,
  "unit": "unidades",
  "geography": {
    "country": "Venezuela",
    "state": "Merida",
    "municipality": "Libertador",
    "locality": "zona centro",
    "precision": "localidad_general"
  },
  "status": "available",
  "observed_date": "2026-07-02",
  "last_updated": "2026-07-02",
  "source": {
    "name": "Acopio comunitario ejemplo",
    "type": "community",
    "contact_public": false
  },
  "permissions": {
    "use": "analysis_and_aggregated_publication",
    "public_allowed": true
  },
  "risk": {
    "pii_risk": "low",
    "sensitive_location": false
  },
  "verification_status": "reported"
}
```

## Estados recomendados

```text
reported
needs_review
verified
available
in_transit
delivered
closed
blocked_pii
```

## Valores de permiso

```text
analysis_only
analysis_and_aggregated_publication
do_not_publish
needs_permission_review
```

## Bloqueo automatico

Un registro debe bloquearse o pasar a revision si contiene:

- nombres de personas afectadas;
- cedulas o documentos;
- telefonos privados;
- direcciones exactas sensibles;
- salud individual;
- informacion de menores;
- personas desaparecidas;
- rutas sensibles;
- texto libre con datos personales.

## Respuesta sugerida

```json
{
  "accepted": true,
  "review_status": "needs_review",
  "public_allowed": false,
  "message": "Registro recibido para revision. No sera publicado automaticamente."
}
```

## Nota metodologica

Este contrato no busca centralizar personas. Busca comparar necesidades, recursos, estados, fuentes, zonas y tiempos para entender coordinacion bajo incertidumbre.
