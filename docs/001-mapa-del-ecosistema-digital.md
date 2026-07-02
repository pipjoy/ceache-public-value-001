# Muchas herramientas ya existen. El problema ahora es que puedan entenderse.

Author: Johaina Chavez
Agency: Ceache Lab
Status: Public draft
Date: 2026-07-02

## Pregunta

Cuando una emergencia produce muchas aplicaciones, formularios, mapas, grupos y listas, la pregunta no es solamente:

```text
Que herramienta falta?
```

La pregunta mas importante es:

```text
Que funciones de coordinacion ya estan cubiertas, por quien, con que datos y bajo que limites?
```

## Que ocurrio

Despues de la crisis, surgio un ecosistema digital amplio: apps de acopio, mapas de danos, directorios, sistemas de busqueda, formularios, bots, hojas de calculo, grupos de WhatsApp, repositorios tecnicos y bases parciales.

Eso no significa desorden por si mismo. Significa que muchas personas intentaron resolver partes distintas de un mismo problema: coordinar ayuda bajo incertidumbre.

## Que cambio

El problema ya no puede describirse solo como falta de herramientas.

La evidencia local muestra otro tipo de problema:

```text
muchas piezas existen,
pero no todas comparten la misma estructura,
el mismo lenguaje,
los mismos criterios de seguridad,
ni la misma forma de conectarse.
```

## Evidencia revisada

Esta lectura parte de evidencia local ya organizada:

| Evidencia | Que contiene |
| --- | --- |
| Matriz plataforma-funcion | 168 fuentes, proyectos o plataformas clasificadas por funcion. |
| Inventario tecnico local | 43 repositorios revisados por viabilidad, preparacion, demo y severidad. |
| Inventario WhatsApp | 23 grupos o canales funcionales de coordinacion. |
| Mi Acopio / Acopio App | Tablas operativas existentes para acopio, necesidades, donaciones, inventario, voluntarios, transporte y trazabilidad. |
| VZLA_DEDUP | Pipeline tecnico para normalizar, deduplicar y proteger datos sensibles. |
| Auditoria API/datasets | Revision inicial de fuentes con senal de API o datos consultables. |
| Observacion longitudinal | Sistema de observacion diaria, preguntas, patrones y auditorias. |

## Cobertura observada

La matriz funcional convierte cada fuente en una o varias funciones operativas. Una misma herramienta puede cubrir mas de una funcion.

| Funcion | Fuentes observadas | Candidatas a interoperar | Senal de API publica | Riesgo PII alto |
| --- | ---: | ---: | ---: | ---: |
| acopio | 25 | 18 | 21 | 6 |
| donaciones | 21 | 9 | 11 | 6 |
| necesidades | 33 | 8 | 17 | 23 |
| refugios | 51 | 19 | 31 | 30 |
| salud | 49 | 18 | 28 | 27 |
| voluntarios | 26 | 8 | 16 | 18 |
| personas desaparecidas | 65 | 4 | 44 | 60 |
| danos | 77 | 36 | 50 | 35 |
| conectividad | 19 | 7 | 10 | 12 |
| informacion verificada | 61 | 26 | 37 | 31 |
| entregas / logistica | 75 | 37 | 49 | 33 |
| datos / API | 82 | 38 | 53 | 44 |

## Que significa

La cantidad de herramientas no garantiza coordinacion.

Para coordinar mejor no basta con publicar otra lista. Hace falta una capa comun que permita comparar funciones:

- que necesidad se reporta;
- en que zona agregada ocurre;
- que estado tiene;
- que fuente la reporta;
- cuando fue actualizada;
- que nivel de confianza tiene;
- que datos pueden compartirse;
- que datos no deben publicarse.

Esa capa comun no reemplaza a las apps existentes. Ayuda a que puedan entenderse.

## Que sabemos

- Existen muchas soluciones, no una sola.
- Varias funciones ya estan parcialmente cubiertas.
- Hay repeticion fuerte en danos, logistica, informacion verificada, personas desaparecidas y datos/API.
- Las funciones mas sensibles no son necesariamente las mas conectables.
- Personas desaparecidas, salud, refugios, menores, ubicaciones exactas y contactos privados requieren proteccion especial.

## Que creemos

- El cuello de botella principal no es crear una app mas.
- El cuello de botella es ordenar datos, funciones, permisos y responsabilidades.
- La mejor contribucion inicial es producir una matriz comun, descargable y revisable.
- Mi Acopio puede servir como nodo demostrador para datos operativos seguros, no como base central de todo el ecosistema.

## Que todavia no sabemos

- Que plataformas siguen activas con datos actualizados.
- Que responsables quieren validar su informacion.
- Que fuentes tienen permiso explicito para compartir datos.
- Que APIs son estables y aptas para integracion.
- Que duplicaciones ayudan y cuales confunden.
- Que campos deben corregirse en inventarios ya existentes.

## Que datos si se pueden compartir

Datos operativos y no personales, por ejemplo:

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

- nombres de personas vulnerables;
- cedulas;
- telefonos privados;
- ubicaciones exactas sensibles;
- datos de salud individual;
- informacion de menores;
- fotos identificables;
- reportes nominales de desaparecidos;
- chats completos de WhatsApp.

## Siguiente paso

La siguiente entrega no debe pedir datos primero.

Debe abrir una validacion:

```text
Si tienes una app, Excel, formulario, API o base operativa,
ayudanos a validar que funcion cubre,
que campos usa,
que datos puede compartir de forma segura
y que informacion no debe exponerse.
```

Primero se muestra el mapa. Despues se pide colaboracion.

## Archivos descargables

- `ecosystem_function_public_table_2026-07-02.csv`: tabla publica por funcion y fuente.
- `common_coordination_item_schema.csv`: esquema minimo para describir una pieza de coordinacion.
- `common_operational_signal_schema.csv`: esquema minimo para reportar una senal operativa.
- `minimum-data-matrix.md`: guia de datos minimos por tipo de operacion.
- `DATA_SAFETY.md`: reglas de seguridad y datos que no deben compartirse.
