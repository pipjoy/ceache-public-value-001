# Declaracion publica - Conversacion para compartir datos seguros

Author: Johaina Chavez
Role: Data Scientist
Agency: Ceache Lab
Document Status: Draft Public Declaration / Pre-convocatoria
Date: 2026-07-02

## Declaracion

Desde Ceache Lab estamos estudiando como se organiza la ayuda durante una emergencia cuando la informacion aparece distribuida entre mapas, formularios, hojas de calculo, apps, telefonos, grupos de mensajeria y reportes publicos.

Despues del Insight 001, hay una observacion inicial clara: existe una huella publica registrada de ayuda, necesidades y puntos de apoyo, pero todavia no permite afirmar cobertura real ni coordinacion efectiva.

Con datos publicos ya pudimos observar puntos de acopio, refugios, servicios de salud, telefonos, zonas reportadas y pedidos de ayuda. En el primer cruce aparecieron 796 puntos operativos publicos, incluyendo acopios, telefonos, refugios y salud. Tambien aparecieron 1.000 zonas reportadas y 2.570 pedidos en una de las fuentes estudiadas.

Eso no significa que sepamos todo. Significa que ya existe una base visible para empezar a entender cobertura, necesidades y coordinacion. Tambien significa que hay un limite importante: los datos estan separados en sistemas distintos, con categorias distintas, estados distintos, fechas distintas y niveles de trazabilidad distintos.

## Que ya se puede observar

Con los datos disponibles hoy, se puede observar:

- donde hay puntos operativos visibles;
- que categorias de ayuda aparecen con mas frecuencia;
- que ciudades concentran mas registros publicos;
- donde aparecen pedidos o zonas reportadas;
- que parte de la ayuda visible esta dentro de Venezuela y que parte aparece desde diaspora;
- que estados operativos existen en algunos sistemas, por ejemplo pendiente, en camino o cubierto.

Esta informacion ya ayuda a hacer mejores preguntas. Permite ver que la respuesta social no parte de cero. Hay personas, organizaciones, voluntarios, plataformas y equipos tecnicos registrando informacion y moviendo ayuda.

Pero una lista visible no equivale a coordinacion completa.

## Que todavia no se puede saber

Con los datos publicos actuales todavia no podemos saber con suficiente confianza:

- que puntos siguen activos hoy;
- que acopios estan llenos, cerrados, saturados o disponibles;
- que pedidos corresponden a necesidades verificadas;
- que pedidos estan duplicados entre plataformas;
- que donaciones llegaron realmente a destino;
- que necesidades fueron cubiertas parcialmente;
- que entregas fueron recibidas por la comunidad;
- que zonas tienen mucha necesidad visible y poca infraestructura visible;
- que informacion existe en hojas privadas, formularios internos o sistemas que aun no publican datos agregados.

Estas limitaciones no son una acusacion contra ningun sistema. Son una condicion normal cuando muchas personas responden al mismo tiempo, bajo presion, con herramientas distintas.

La pregunta ahora no es quien tiene "la base completa". La pregunta es que datos seguros pueden conversar entre si para mejorar decisiones sin exponer personas.

## Que datos seguros podemos recibir

Ceache Lab abre primero una conversacion metodologica para identificar que datos operativos seguros, agregados y trazables podrian compartirse. Esta no es una recepcion masiva de archivos crudos.

No subas ni envies archivos originales si contienen datos personales. Si una fuente mezcla datos sensibles con datos operativos, comparte primero solo metadatos o una version agregada.

Los datos seguros pueden tratar sobre:

- acopios;
- refugios;
- donaciones;
- necesidades;
- voluntariado agregado;
- entregas y logistica;
- puntos de salud o servicios, solo si la informacion es publica, operativa y no individual;
- plataformas, formularios, mapas o sistemas que ya registran informacion de ayuda.

Los datos mas utiles no son necesariamente los mas detallados. Los campos minimos que ayudan a coordinar son:

- tipo de registro;
- categoria o subcategoria;
- pais, estado, municipio, ciudad o zona agregada;
- estado operativo;
- fecha de reporte o ultima actualizacion;
- fuente;
- enlace de fuente, si existe;
- nivel de confianza o metodo de verificacion, si existe;
- restriccion de publicacion;
- licencia o permiso de uso;
- etapa de la cadena, por ejemplo reportado, verificado, recibido en centro, asignado, en camino, distribuido, recibido o no confirmado.

Para acopios, refugios y donaciones, tambien pueden ser utiles campos como capacidad estimada, disponibilidad, categorias que recibe, categorias que necesita, horario publico o contacto institucional publico.

Para entregas, lo mas importante es distinguir promesa, stock, despacho, transito, llegada, distribucion y recepcion. No es lo mismo que una ayuda haya sido ofrecida, enviada, distribuida o confirmada como recibida.

## Que datos no se deben enviar

No pedimos ni queremos recibir datos personales.

Por favor no enviar:

- nombres de personas afectadas;
- cedulas, documentos de identidad o pasaportes;
- telefonos privados;
- direcciones exactas de hogares;
- ubicaciones sensibles;
- datos de menores;
- informacion individual de salud;
- listas nominales de personas alojadas en refugios;
- datos de personas desaparecidas;
- datos de salud individual o casos clinicos;
- rutas vulnerables o informacion logistica que pueda poner en riesgo a comunidades, voluntarios u organizaciones;
- capturas de chats privados con datos identificables.

En esta fase, Ceache Lab no recibira listas nominales de personas desaparecidas, datos de menores, salud individual, chats privados, fotos identificables, rutas sensibles ni datos de hogares. Si existe una obligacion humanitaria o legal relacionada con informacion sensible, debe tratarse por un canal separado y especializado, no por esta convocatoria.

Si una fuente contiene datos personales mezclados con datos operativos, se debe compartir solo una version segura: agregada, anonimizada, con campos sensibles removidos o con ubicaciones reducidas a zona, municipio, ciudad o estado, segun el riesgo.

Interoperar no significa juntar datos de personas. Para esta convocatoria, el principio es otro:

```text
Interoperar funciones, no personas.
```

## Como compartir datos

La primera accion recomendada es registrar la fuente y conversar sobre la estructura de datos antes de enviar archivos.

Cuando exista una version segura, los datos pueden compartirse en cualquiera de estos formatos:

- CSV;
- Excel;
- Google Sheet;
- API;
- formulario;
- export agregado desde una app, mapa o sistema interno.

Si compartes CSV o Excel, incluye una fila de encabezados clara y, si es posible, una breve descripcion de cada columna. No compartas el archivo original si contiene nombres, telefonos privados, documentos, direcciones exactas, salud individual, menores, desaparecidos, fotos identificables, chats privados o texto libre sensible.

Si compartes Google Sheet, puedes enviar una URL con permisos de lectura o una copia segura sin datos personales.

Si compartes una API, incluye la URL del endpoint, descripcion de campos, frecuencia de actualizacion, restricciones de uso y canal tecnico o institucional. No envies muestras reales si contienen PII; primero comparte esquema, documentacion o datos de ejemplo anonimizados.

Si no tienes una base estructurada, puedes registrar la fuente mediante formulario y explicar que tipo de informacion existe, quien la mantiene, cada cuanto se actualiza y que version podria compartirse sin riesgo.

Si el sistema todavia no puede exportar datos, tambien sirve conversar sobre estructura: que registra, donde aplica, cuando se actualiza, que estados usa y que campos no deben salir del sistema original.

## Atribucion, licencia, reciprocidad y seguridad

Ceache Lab dara atribucion a las fuentes cuando la fuente autorice ser nombrada y cuando hacerlo no aumente riesgos.

Cada envio debe indicar una condicion de uso:

- datos publicos reutilizables;
- datos compartidos para analisis interno;
- datos compartidos solo para validacion metodologica;
- datos que pueden publicarse de forma agregada;
- datos que no deben publicarse.

La licencia o permiso debe quedar claro antes de integrar cualquier fuente a un dataset publico. Si no hay permiso claro, Ceache Lab no tratara esos datos como publicables.

Cada fuente puede indicar condiciones de uso, pedir revision de atribucion y decidir si su aporte puede ser publico, agregado, interno o solo metodologico. Compartir una fuente no obliga a publicarla.

Ceache Lab separara tres niveles de trabajo:

- datos recibidos;
- datos normalizados para analisis;
- datos publicables.

No todo dato recibido sera publicado. La publicacion dependera de controles de seguridad, riesgo de identificacion, permiso de uso, calidad de fuente y utilidad publica.

Cuando haya duda, se reducira el nivel de detalle. Una ubicacion exacta puede convertirse en zona agregada. Un contacto privado puede eliminarse. Un registro sensible puede quedar fuera del dataset publico.

La publicacion no se decide campo por campo de forma aislada. Una combinacion de zona, fecha, categoria, cantidad, fuente y estado puede ser sensible aunque cada campo parezca seguro por separado.

## Para que se usaran los datos

Los datos seguros se usaran, con permiso y controles, para producir analisis publicos sobre cobertura, necesidades, capacidad, disponibilidad, estado operativo, brechas de informacion e interoperabilidad entre sistemas.

El objetivo no es reemplazar las apps ni centralizar a la fuerza el trabajo de quienes ya estan respondiendo. El objetivo es ayudar a que la informacion critica pueda circular mejor entre fuentes, sin obligar a todas las organizaciones a usar una sola herramienta.

La primera capa sera simple:

```text
tema + geografia agregada + tiempo + estado + fuente
```

Con eso se puede empezar a comparar necesidad visible con ayuda visible, identificar brechas de informacion o coordinacion, evitar duplicacion y mostrar que informacion falta para coordinar mejor.

## Cierre

Esta conversacion parte de una evidencia inicial: ya hay una huella publica registrada de ayuda. Ahora hace falta una capa comun de datos seguros para entender cobertura, necesidades, donaciones, refugios, voluntariado y entregas sin exponer personas.

Si tienes una hoja, formulario, mapa, app, API, registro interno o export agregado que pueda ayudar a entender la respuesta, puedes conversar con Ceache Lab sobre como preparar una version segura.

No buscamos mas datos por acumular datos.

Buscamos los datos minimos que permitan cuidar mejor la coordinacion, la atribucion, la licencia y la seguridad.
