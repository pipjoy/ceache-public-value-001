# Insight 001 - Hay una huella publica de ayuda, pero los datos todavia no permiten ver coordinacion completa

Author: Johaina Chavez
Agency: Ceache Lab
Document Status: Laboratory Insight / Publicable Draft
Date: 2026-07-02

## Pregunta

Que podemos entender hoy, usando solo evidencia local ya disponible, al mirar juntos puntos de acopio, telefonos, refugios, servicios de salud, zonas reportadas y pedidos de ayuda?

## Resumen

Con datos publicos ya reunidos por Ceache Lab se observa una huella publica registrada alrededor de la crisis. Hay puntos de acopio, telefonos, refugios, servicios de salud, zonas reportadas y pedidos con estado operativo.

La evidencia disponible sugiere que una limitacion importante no es solo la ausencia de datos. Tambien importa que los datos estan repartidos en sistemas distintos, con categorias distintas, estados distintos, fechas distintas y niveles de trazabilidad distintos.

Eso puede limitar la coordinacion observable desde datos publicos. Si una organizacion ve un punto abierto, otra ve un pedido pendiente y otra ve una zona reportada, todavia falta una capa comun que permita responder preguntas basicas: donde hay cobertura visible, donde hay necesidad visible, que esta en camino, que fue recibido y que sigue sin confirmar.

## Que sabemos

Nota metodologica:

- fecha de corte: 2026-07-02;
- fuentes principales: `data/public_operational_points_clean.csv`, `data/week2/apoyo_zonas_all.json`, `data/week2/apoyo_pedidos_all.json` y `outputs/api_dataset_summary.json`;
- unidad de conteo: registros visibles en archivos locales, no capacidad real ni cobertura efectiva;
- limpieza: ciudades contadas por `city_key` normalizada cuando existe;
- limitaciones: puede haber duplicados, registros desactualizados, diferencias de criterio entre plataformas y puntos que ya no esten operativos. Los registros mezclan objetos distintos: acopios, telefonos, refugios y salud no equivalen operacionalmente.

En el dataset limpio de puntos operativos publicos aparecen 796 registros.

| Tipo de punto | Registros |
| --- | ---: |
| Acopio | 654 |
| Telefono | 78 |
| Refugio | 49 |
| Salud | 15 |

La mayor parte de los puntos visibles estan en Venezuela, pero tambien aparecen puntos de apoyo fuera del pais.

| Pais | Registros |
| --- | ---: |
| Venezuela | 574 |
| Estados Unidos | 94 |
| Colombia | 51 |
| Espana | 15 |
| Ecuador | 14 |
| Mexico | 11 |

Las ciudades con mas puntos visibles, contando por clave de ciudad normalizada para unir variantes de escritura, son:

| Ciudad | Registros |
| --- | ---: |
| Caracas | 191 |
| Merida | 37 |
| Maracaibo | 28 |
| Ciudad Bolivar | 23 |
| Ciudad Guayana | 19 |
| Valencia | 19 |

Las categorias mas repetidas en puntos operativos son:

| Categoria | Registros |
| --- | ---: |
| Agua | 407 |
| Ropa | 369 |
| Medicamentos | 362 |
| Alimentos | 259 |
| Alimentos no perecederos | 219 |
| Frazadas | 132 |
| Higiene | 126 |

En los archivos locales de ApoyoVenezuela aparecen 1.000 zonas reportadas y 2.570 pedidos. En esos pedidos, el estado dominante es pendiente.

| Estado de pedido | Registros |
| --- | ---: |
| Pendiente | 2.553 |
| En camino | 16 |
| Cubierto | 1 |

Estos datos no prueban por si solos cobertura real ni entrega final. Si prueban algo mas basico y valioso: ya existe una huella publica de actividad operativa registrada que puede ordenarse, compararse y mejorar.

## Que creemos que significa

Los registros visibles sugieren una estructura minima:

- lugares donde llevar o buscar ayuda;
- canales de contacto;
- zonas donde se reportan danos o necesidades;
- pedidos con estado operativo;
- categorias recurrentes de ayuda;
- senales de apoyo desde la diaspora.

Pero esa estructura todavia no equivale a coordinacion completa.

Un punto abierto no prueba que tenga capacidad suficiente. Un pedido pendiente no prueba abandono. Una entrega en camino no prueba recepcion. Una categoria repetida no prueba prioridad real sin fecha, zona, fuente, estado y nivel de confianza.

Por eso los datos interoperables no son un lujo tecnico. Son una condicion importante para mejorar la coordinacion.

Cuando los datos estan conectados de forma segura, ayudan a separar cosas que en una crisis suelen mezclarse: necesidad reportada, necesidad verificada, oferta disponible, donacion recibida, ayuda asignada, ayuda en transito, ayuda distribuida y recepcion confirmada.

Esa diferencia importa porque permite coordinar mejor sin obligar a todos a usar la misma aplicacion. Una hoja de calculo, un formulario, una API, un mapa o una lista pueden seguir existiendo por separado, siempre que compartan un minimo comun: que registran, donde aplica, cuando se actualizo, en que estado esta y que puede publicarse sin exponer personas.

## Que todavia no sabemos

No sabemos todavia:

- que pedidos corresponden a necesidades verificadas;
- que pedidos duplican reportes de otras plataformas;
- que puntos siguen activos hoy;
- que acopios estan llenos, cerrados o saturados;
- que donaciones llegaron a destino;
- que necesidades fueron cubiertas parcialmente;
- que regiones tienen mucha necesidad visible y poca infraestructura visible;
- que datos estan en hojas de calculo privadas, formularios o grupos de mensajeria;
- que informacion no debe conectarse por riesgo de privacidad, seguridad o reidentificacion.

Estas ausencias no invalidan los datos existentes. Sugieren donde una capa comun podria aportar valor.

## Por que estos datos son necesarios para coordinar mejor

Para coordinar mejor no basta saber que existe una app, un mapa o una lista.

Hace falta que cada fuente pueda responder preguntas simples:

```text
Que registra?
Donde aplica?
Cuando fue actualizado?
En que estado esta?
Quien lo reporta?
Que nivel de confianza tiene?
Que datos pueden compartirse sin exponer personas?
```

Sin esas respuestas, la ayuda puede verse mas organizada de lo que realmente esta. Puede haber muchos puntos en una ciudad y aun asi faltar agua en una zona especifica. Puede haber muchos pedidos pendientes y aun asi no saber cuales son duplicados. Puede haber una donacion prometida y aun asi no saber si fue recibida.

Con esas respuestas, en cambio, se pueden construir comparaciones utiles:

- necesidad visible frente a infraestructura visible;
- pedido reportado frente a pedido verificado;
- ayuda ofrecida frente a ayuda recibida;
- zona con dano reportado frente a punto operativo cercano;
- categoria solicitada frente a categoria disponible;
- estado declarado frente a ultima actualizacion.

El objetivo no es crear una base maestra de personas. El objetivo es conectar datos operativos agregados, trazables y seguros para que las decisiones sean menos ciegas.

## Dato minimo recomendado

Para acopios, refugios, pedidos, donaciones y entregas, los campos mas importantes no son tecnicos. Son operativos:

- categoria;
- zona agregada;
- estado;
- fecha de actualizacion;
- fuente;
- nivel de confianza;
- restriccion de publicacion;
- etapa de la cadena: reportado, verificado, en camino, distribuido, recibido o no confirmado.

Tambien es importante decir que no deberia circular en una capa publica: nombres de personas vulnerables, cedulas, telefonos privados, direcciones sensibles, datos de menores, informacion individual de salud o cualquier dato que facilite reidentificacion.

## Declaracion provisional

Ceache Lab no necesita reemplazar las herramientas que surgieron durante la crisis. Puede ayudar a que sus datos seguros conversen.

La primera conclusion publica es esta:

> Ya existe una huella publica y registrada de ayuda, necesidades y puntos de apoyo. Todavia no permite afirmar cobertura real ni coordinacion efectiva. El siguiente paso es construir una capa comun de datos seguros para comparar necesidad, oferta, estado y entrega sin exponer personas.

## Siguiente paso de trabajo

Antes de pedir mas datos, Ceache Lab debe demostrar valor con los datos que ya tiene:

1. publicar este primer insight;
2. producir una matriz minima de datos para acopios, necesidades, donaciones, refugios y entregas;
3. identificar que campos son compartibles y que campos no deben circular;
4. preparar una convocatoria clara solo despues de mostrar que conectar datos mejora la coordinacion.

En esta fase, Ceache Lab no solicita datos personales ni bases nominales. El trabajo inmediato se concentra en datos operativos agregados, trazables y seguros.

## Evidencia local utilizada

Esta pieza se basa en evidencia local existente en el workspace:

- `data/public_operational_points_clean.csv`;
- `data/week2/apoyo_zonas_all.json`;
- `data/week2/apoyo_pedidos_all.json`;
- `outputs/api_dataset_summary.json`;
- `docs/research/plans/data-value-and-interoperability-plan.md`;
- `docs/research/plans/next-72-hours-execution-plan.md`;
- `docs/longitudinal/evidence-registry.md`.

Los conteos de puntos operativos, tipos de punto, paises, ciudades normalizadas, categorias y estados de pedido fueron verificados contra esos archivos locales el 2026-07-02.
