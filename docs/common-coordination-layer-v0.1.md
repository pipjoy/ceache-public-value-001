# Capa comun de coordinacion v0.1

Version: 0.1  
Fecha: 2026-07-02

## Pregunta

Como se conectan grupos de coordinacion, aplicaciones, hojas, APIs y repositorios tecnicos sin convertir la emergencia en una base centralizada de personas?

## Observacion

La respuesta ya no parte de cero.

La evidencia local muestra al menos cuatro capas activas:

- grupos de coordinacion por funcion: datos, acopio, WhatsApp/SMS, ingenieria civil, producto, responsables, refugio, discapacidad, menores, busqueda de personas;
- desarrollo tecnico para ingesta, limpieza, deduplicacion, PII masking, staging, canonicalizacion y API publica;
- fuentes operativas visibles: acopios, refugios, telefonos, pedidos, zonas, necesidades y plataformas;
- hojas, formularios y sistemas que ya producen datos, aunque no siempre con el mismo formato.

La pregunta no es como reemplazar esas capas.

La pregunta es que minimo deben compartir para poder coordinar.

## Hipotesis

Una capa comun minima puede reducir duplicacion y costo de coordinacion si conecta:

```text
funcion + zona + tiempo + estado + fuente + permiso + riesgo
```

sin conectar:

```text
nombre + cedula + telefono + direccion exacta + foto + chat crudo
```

## Que sabemos

- WhatsApp funciona como infraestructura de coordinacion, pero no debe tratarse como base de datos.
- VZLA_DEDUP ya trabaja con entidades, normalizacion, deduplicacion, HMAC, cuarentena, staging y API.
- Las fuentes de acopio y pedidos tienen valor operativo, pero no prueban cobertura real ni entrega final.
- Los datos de personas desaparecidas, menores, salud, rutas y ubicaciones sensibles requieren una capa de proteccion distinta.
- La interoperabilidad util no necesita empezar por una base unica; puede empezar por metadatos, funciones y estados.

## Que creemos

Una capa comun debe tener dos registros principales:

1. `common_coordination_item`: registra que existe una fuente, grupo, proyecto, hoja, app, decision, tarea o riesgo.
2. `common_operational_signal`: registra una senal operativa agregada: necesidad, oferta, acopio, refugio, voluntariado, entrega, dano, conectividad o informacion verificada.

El primer registro conecta coordinacion.

El segundo conecta datos operativos.

Ninguno necesita identificar personas.

## Que todavia no sabemos

- Que grupos aceptaran compartir resumenes diarios.
- Que proyectos tienen permiso para integrarse.
- Que fuentes pueden exportar datos agregados.
- Que campos se mantienen actualizados.
- Que datos se vuelven inseguros al cruzarse con otros.
- Que parte del sistema requiere revision humana antes de interoperar.

## Unidad comun

La unidad comun no es una persona.

La unidad comun es una relacion observable:

```text
evento
fuente
funcion
zona agregada
categoria
estado
tiempo
permiso
riesgo
```

## Capa 1: indice de coordinacion

Usar cuando aparece:

- grupo de WhatsApp;
- proyecto;
- repo;
- hoja;
- API;
- formulario;
- decision;
- tarea;
- riesgo;
- responsable por rol;
- necesidad de schema;
- dependencia entre proyectos.

Archivo:

```text
schemas/common_coordination_item_schema.csv
```

Ejemplo de uso:

```text
Grupo 1: Unificar Data -> data_integration -> necesita mapear fuentes y permisos -> riesgo medio -> metadata_only
```

No se copia el chat.

Se registra la funcion.

## Capa 2: senal operativa

Usar cuando aparece:

- necesidad agregada;
- oferta de donacion;
- punto de acopio;
- refugio;
- capacidad voluntaria;
- entrega;
- dano;
- conectividad;
- informacion verificada.

Archivo:

```text
schemas/common_operational_signal_schema.csv
```

Ejemplo de uso:

```text
necesidad -> agua -> Merida / municipio agregado -> reportada -> 2026-07-02 -> fuente B -> publicacion agregada permitida
```

No se registra la persona que pidio ayuda.

Se registra la senal.

## Mapeo de la realidad observada

| Capa existente | Que aporta | Entra a la capa comun como | Que no debe entrar |
|---|---|---|---|
| Grupos WhatsApp | decisiones, tareas, proyectos, fuentes, riesgos | `common_coordination_item` | mensajes crudos, telefonos, nombres privados |
| Grupo Unificar Data | schemas, catalogos, permisos, normalizacion | `common_coordination_item` | datos nominales |
| VenezuelaDataCrisis / VZLA_DEDUP | pipeline, deduplicacion, PII masking, staging, canonical, API | metadatos de fuente, estado de integracion, agregados permitidos | personas nominales, fotos, cedulas, salud individual |
| Acopio / Mi Acopio / AcopioVE | puntos, necesidades, categorias, estado operativo | `common_operational_signal` | inventario sensible, rutas, contactos privados |
| Soluciones WhatsApp & SMS | canal de recepcion e ingestion | `common_coordination_item` y senales filtradas | chats completos |
| Ingenieria civil | danos, inspecciones, prioridades tecnicas | senales agregadas de dano o evaluacion | ubicaciones sensibles sin permiso |
| Menores / discapacidad / psicosocial | protocolos, necesidades agregadas, recursos | metadatos y agregados | casos individuales |
| Periodistas / comunicaciones | difusion y explicacion publica | decision o tarea de comunicacion | datos operativos sensibles |

## Estados recomendados

Para coordinacion:

```text
observed
needs_owner
needs_permission
needs_pii_review
mapped
in_progress
blocked
ready_to_share
internal_only
archived
```

Para senales operativas:

```text
reported
needs_review
verified
active
partially_addressed
covered
expired
contradictory
blocked_pii
archived
```

## Permisos recomendados

```text
public
aggregate_public
metadata_only
internal_only
needs_permission
do_not_share
```

## Regla de publicacion

Una senal puede publicarse si cumple:

- no identifica personas;
- no expone ubicacion sensible;
- no revela ruta activa;
- no contiene salud individual;
- no contiene menores o desaparecidos nominales;
- tiene fuente;
- tiene fecha;
- tiene permiso;
- puede explicarse con limitaciones.

## Que refutaria esta hipotesis

La hipotesis se debilita si:

- los grupos no pueden producir resumenes sin copiar chats;
- los proyectos no tienen exportaciones o metadatos minimos;
- las fuentes no pueden declarar permisos;
- la agregacion elimina tanta informacion que ya no sirve para coordinar;
- los riesgos de reidentificacion siguen altos incluso con campos minimos.

## Que la fortaleceria

La hipotesis se fortalece si:

- varios grupos logran reportar proyectos, fuentes, tareas y riesgos con el mismo indice;
- hojas, apps y APIs pueden mapearse sin cambiar sus sistemas internos;
- las senales agregadas permiten detectar duplicaciones, brechas o datos vencidos;
- VZLA_DEDUP puede exponer solo agregados o metadatos utiles para coordinacion sin filtrar personas;
- el costo de coordinacion baja: menos mensajes repetidos, menos dudas sobre fuente, mas claridad sobre siguiente accion.

## Nueva pregunta

Que parte de la coordinacion necesita datos estructurados y que parte solo necesita mejores resumenes, permisos y responsables?
