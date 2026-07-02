# Datos seguros para entender la respuesta

Johaina Chavez
Data Scientist
Ceache Lab

Document Status: Public Value Package
Date: 2026-07-02

## Resumen ejecutivo

Ceache Lab reviso datos publicos, inventarios de plataformas, APIs, hojas de calculo, mapas, puntos operativos, zonas reportadas y pedidos de ayuda relacionados con la respuesta a la crisis venezolana de 2026.

La primera conclusion responsable es esta:

> Existe una huella publica y registrada de ayuda, necesidades y puntos de apoyo, pero la evidencia disponible no permite afirmar cobertura real ni coordinacion efectiva.

El valor de este primer paquete no esta en decir que ya sabemos todo. Esta en mostrar que ya podemos hacer mejores preguntas con datos existentes, y tambien en explicar que datos seguros harian falta para coordinar mejor sin exponer personas.

## Que observamos

### Puntos, zonas y pedidos

En los archivos locales revisados aparecen:

| Elemento observado | Conteo |
| --- | ---: |
| Puntos operativos publicos | 796 |
| Acopios | 654 |
| Telefonos | 78 |
| Refugios | 49 |
| Salud | 15 |
| Zonas reportadas en ApoyoVenezuela | 1.000 |
| Pedidos en ApoyoVenezuela | 2.570 |
| Pedidos pendientes | 2.553 |
| Pedidos en camino | 16 |
| Pedidos cubiertos | 1 |

Estos conteos muestran registros visibles. No prueban capacidad real, vigencia, cobertura efectiva, recepcion final ni ausencia de duplicados.

### Ecosistema digital

El Atlas 001 registra:

| Elemento observado | Conteo |
| --- | ---: |
| Fuentes/plataformas consolidadas | 168 |
| Relaciones posibles en matriz | 6.346 |
| Fuentes con mas de una funcion observable | 120 |
| Fuentes con riesgo PII alto | 60 |
| Relaciones con nota PII-safe | 1.770 |

Funciones mas visibles:

| Funcion | Plataformas |
| --- | ---: |
| Datos/API | 82 |
| Danos | 77 |
| Entregas/logistica | 75 |
| Personas desaparecidas | 65 |
| Informacion verificada | 61 |
| Refugios | 51 |
| Salud | 49 |

Esto no significa que esas plataformas tengan impacto probado. Significa que existe un ecosistema digital observable, con funciones repetidas, riesgos distintos y posibilidades de interoperabilidad segura en algunos casos.

## Que significa

La respuesta visible no parte de cero. Hay puntos, listas, plataformas, APIs, formularios, mapas, hojas de calculo y equipos registrando informacion.

Pero los datos visibles todavia no permiten responder con suficiente confianza preguntas operativas basicas:

- que punto sigue activo hoy;
- que pedido fue verificado;
- que ayuda esta en camino;
- que ayuda fue recibida;
- que acopio esta saturado;
- que refugio tiene capacidad;
- que necesidad esta cubierta parcialmente;
- que informacion se repite entre plataformas;
- que dato no debe circular por riesgo.

El problema no es solo tener mas datos. El problema es tener datos comparables, trazables, actualizados y seguros.

## La propuesta de Ceache Lab

Ceache Lab propone una capa minima de datos seguros para comparar:

```text
necesidad
oferta
estado
entrega
fuente
tiempo
geografia agregada
```

La regla central es:

```text
Interoperar funciones, no personas.
```

Eso significa conectar informacion operativa sin construir una base maestra de individuos.

La llave recomendada para conectar sistemas es:

```text
function + geography + time
```

La llave prohibida es:

```text
nombre + cedula + telefono + direccion exacta
```

## Que datos ayudan

Para acopios, donaciones, necesidades, refugios, voluntariado y entregas, los campos mas utiles son operativos:

- categoria;
- zona agregada;
- estado;
- fecha de actualizacion;
- fuente;
- permiso/licencia;
- nivel de confianza;
- restriccion de publicacion;
- etapa de la cadena.

Para entregas, la diferencia critica es separar:

```text
prometida
en_stock
despachada
en_transito
llegada
distribuida
recibida
no_confirmada
```

No es lo mismo ayuda prometida que ayuda recibida.

## Que datos no deben circular

Ceache Lab no debe recibir ni publicar:

- nombres de personas afectadas;
- cedulas o documentos;
- telefonos privados;
- direcciones exactas de hogares;
- ubicaciones sensibles;
- datos de menores;
- salud individual;
- listas nominales de personas alojadas;
- personas desaparecidas;
- fotos identificables;
- chats privados;
- rutas vulnerables;
- texto libre con informacion personal.

Tambien debe revisarse el riesgo por combinacion. Una zona, fecha, categoria, cantidad, fuente y estado pueden ser sensibles aunque cada campo parezca seguro por separado.

## Que se entrega en este paquete

### 1. Insight 001

[Insight 001 - Hay una huella publica de ayuda, pero los datos todavia no permiten ver coordinacion completa](insight-001-infraestructura-visible-ayuda.md)

Explica que se puede observar hoy con datos publicos y que no se puede afirmar todavia.

### 2. Atlas 001

[Atlas 001 - Ecosistema digital de emergencia Venezuela 2026](../research/plans/atlas-001-ecosistema-digital.md)

Clasifica apps, sistemas, hojas de calculo, APIs, repositorios, mapas, directorios y plataformas por funcion observable.

### 3. Matriz minima de datos compartibles

[Matriz minima de datos compartibles](../research/plans/minimum-data-matrix.md)

Define los campos minimos para acopios, donaciones, necesidades, refugios, voluntariado, entregas y catalogo de fuentes.

### 4. Contrato de schemas v0.1.0

[Contrato de schemas v0.1.0](../research/plans/schema-contract-v0.1.0.md)

Declara campos transversales necesarios antes de publicar datasets normalizados.

### 5. Herramienta minima v0.1

[Herramienta minima de recepcion segura de datos v0.1](../research/plans/data-intake-tool-v0.md)

Disena un flujo de intake, catalogo, mapeo, validacion y decision humana. No habilita publicacion automatica.

### 6. Pre-convocatoria

[Declaracion publica - Conversacion para compartir datos seguros](declaracion-convocatoria-datos-seguros.md)

Abre una conversacion metodologica para preparar datos seguros. No abre recepcion masiva de archivos crudos.

## Que no prometemos todavia

Ceache Lab no promete:

- coordinacion completa;
- cobertura real por zona;
- recepcion final de ayuda;
- interoperabilidad automatica;
- verificacion de todas las apps;
- base maestra de personas;
- deduplicacion nominal;
- procesamiento de salud individual;
- manejo publico de personas desaparecidas;
- publicacion automatica de fuentes externas.

## Como publicar esto

### Publicacion 1

Publicar Insight 001 para mostrar valor con evidencia disponible.

### Publicacion 2

Publicar una version breve de la matriz minima para explicar que datos ayudan y que datos no deben circular.

### Publicacion 3

Publicar Atlas 001 para mostrar que la crisis produjo un ecosistema digital de funciones, no solo una lista de apps.

### Publicacion 4

Publicar la pre-convocatoria para invitar a conversar sobre datos seguros despues de demostrar valor.

### Publicacion 5

Probar un piloto con 3-5 fuentes para validar el proceso antes de construir una herramienta completa.

## Primer mensaje publico

> Como cientifica de datos, mi primera pregunta no es quien tiene todos los datos. Es que podemos entender con los datos seguros que ya existen, y que nos falta para coordinar mejor sin exponer personas.
>
> En Ceache Lab encontramos una huella publica registrada de ayuda: puntos de acopio, telefonos, refugios, salud, zonas reportadas y pedidos. Pero esa huella todavia no permite afirmar cobertura real ni coordinacion efectiva.
>
> El siguiente paso no es centralizar todo. Es construir una capa minima de datos seguros para comparar necesidad, oferta, estado y entrega.

## Proximo paso

Publicar Insight 001 y preparar una pieza breve de la matriz minima.

La frase guia:

> Recibido no significa publicable. Visible no significa verificado. Conectar datos no significa conectar personas.
