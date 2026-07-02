# Ceache Public Value Package 001

**Datos seguros para entender la respuesta**  
Johaina Chavez, Data Scientist  
Ceache Lab  
Fecha: 2026-07-02

Este repositorio publica la primera entrega abierta de Ceache Lab sobre datos, ayuda e interoperabilidad durante la crisis venezolana de 2026.

La idea central es simple:

> Hay una huella publica de ayuda, necesidades y sistemas digitales, pero la evidencia disponible todavia no permite afirmar cobertura real ni coordinacion efectiva.

## Para cualquier persona

Ceache reviso registros publicos, listas, apps, hojas de calculo, APIs, mapas y sistemas que aparecieron durante la respuesta a la crisis.

Encontramos evidencia visible de:

- 796 puntos operativos publicos.
- 2.570 pedidos registrados en una fuente revisada.
- 1.000 zonas reportadas.
- 168 fuentes, apps, listas o sistemas clasificados.

Eso no significa que toda la ayuda haya llegado, ni que todo este coordinado. Significa que ya existe informacion suficiente para hacer mejores preguntas:

- Que punto sigue activo?
- Que pedido fue verificado?
- Que ayuda esta en camino?
- Que ayuda fue recibida?
- Que acopio esta saturado?
- Que dato no deberia circular?

## Para equipos tecnicos

Este repositorio contiene:

- documentos publicables de analisis;
- matriz minima de datos compartibles;
- contrato de schemas;
- schemas CSV para acopios, donaciones, necesidades, refugios, voluntarios, entregas y catalogo de fuentes;
- matriz plataforma-funcion del Atlas 001;
- propuesta de intake seguro para CSV, Excel, Google Sheet, formulario o API.
- kit de intake para recibir contexto desde acopios, voluntarios, transportistas, organizaciones y equipos tecnicos.
- guia rapida para compartir datos seguros;
- checklist de calidad de datos;
- plantilla tipo Google Sheet/CSV;
- contrato API minimo para interoperabilidad segura.

Las plataformas nombradas en `atlas/platform_function_matrix.csv` aparecen como fuentes observadas del ecosistema digital. Su inclusion no implica afiliacion, recomendacion, validacion de impacto ni aprobacion por parte de Ceache Lab.

La regla metodologica central es:

> Interoperar funciones, no personas.

La llave recomendada para comparar sistemas es:

```text
function + geography + time
```

La llave prohibida es:

```text
nombre + cedula + telefono + direccion exacta
```

## Estructura del repositorio

```text
docs/
  paquete-valor-publico-001.md
  insight-001-infraestructura-visible-ayuda.md
  atlas-001-ecosistema-digital.md
  minimum-data-matrix.md
  schema-contract-v0.1.0.md
  data-intake-tool-v0.md
  declaracion-convocatoria-datos-seguros.md
  quick-start-compartir-datos.md

schemas/
  acopios_schema.csv
  donaciones_schema.csv
  necesidades_schema.csv
  refugios_schema.csv
  voluntarios_schema.csv
  entregas_schema.csv
  source_catalog_schema.csv

atlas/
  platform_function_matrix.csv

downloads/
  ceache-paquete-valor-001.zip

intake-kit/
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

Si eres una organizacion, comunidad o equipo tecnico:

1. Lee `docs/minimum-data-matrix.md`.
2. Revisa el schema CSV que corresponde a tu tipo de dato.
3. Lee `docs/quick-start-compartir-datos.md`.
4. Usa `intake-kit/data-quality-checklist.md` antes de compartir.
5. Copia `intake-kit/google_sheet_template.csv` como base de tu hoja.
6. No compartas datos personales ni ubicaciones sensibles.
7. Compara tus campos con los schemas.
8. Contacta a Ceache Lab si quieres mapear una hoja, app, formulario o API a un formato seguro.

## Siguiente valor: intake de contexto

El directorio `intake-kit/` convierte la metodologia en una herramienta practica.

Permite recibir:

- relatos desde el terreno;
- datos operativos minimos;
- disponibilidad de transporte;
- necesidades por zona agregada;
- ofertas de donacion;
- fuentes tecnicas como hojas, apps o APIs.
- plantillas copiables para iniciar una hoja segura;
- contratos minimos para conectar sistemas.

El objetivo no es capturar todo. Es recibir senales seguras que puedan transformarse en evidencia revisable.

## Que no contiene

Este repositorio no contiene:

- nombres de personas afectadas;
- cedulas o documentos;
- telefonos privados;
- direcciones exactas;
- salud individual;
- listas nominales de refugios;
- personas desaparecidas;
- chats privados;
- fotos identificables.

## Que trabajo hicimos

1. Consolidamos evidencia publica disponible.
2. Clasificamos fuentes, apps, hojas, APIs y sistemas por funcion observable.
3. Separamos lo que se puede saber de lo que todavia no se puede afirmar.
4. Definimos una matriz minima de datos compartibles.
5. Creamos schemas CSV para que equipos tecnicos puedan comparar sus datos.
6. Documentamos riesgos PII y reglas de publicacion segura.
7. Preparamos una propuesta de intake para recibir datos sin publicar informacion sensible automaticamente.

## Entregables descargables

- Paquete completo: `downloads/ceache-paquete-valor-001.zip`
- Documentos: `docs/`
- Schemas tecnicos: `schemas/`
- Matriz plataforma-funcion: `atlas/platform_function_matrix.csv`
- Kit de intake: `intake-kit/`
- Guia rapida: `docs/quick-start-compartir-datos.md`
- Checklist de calidad: `intake-kit/data-quality-checklist.md`
- Plantilla tipo Google Sheet: `intake-kit/google_sheet_template.csv`
- API contract minimo: `intake-kit/API_CONTRACT_MINIMO.md`

## Estado

Version: `v0.1.0`  
Estado: public value package, evidencia preliminar  
Licencia: ver `LICENSE.md`  
Contacto: ceachelab@gmail.com
