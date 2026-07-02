# Atlas 001 - Ecosistema digital de emergencia Venezuela 2026

Fecha de corte: 2026-07-02.

Este atlas clasifica apps, sistemas, hojas de calculo, APIs, repositorios, mapas, directorios y plataformas surgidas o registradas durante la crisis. La lectura se limita a funcion observable en inventario, auditoria de API y matriz de conexiones; no evalua impacto social si no hay evidencia directa.

## Fuentes leidas

- `data/connected_platform_inventory.csv`
- `outputs/platform_connection_matrix.csv`
- `outputs/api_live_audit.csv`
- `docs/research/programs/programa-03-ecosistema-digital-emergencia.md`
- `docs/research/plans/data-value-and-interoperability-plan.md`

## Metodo de clasificacion

La unidad de analisis es la funcion, no la plataforma. Cada fuente puede cumplir varias funciones. La clasificacion usa `topics`, nombre, URL, descripcion, tags, senales de API y campos abiertos del inventario.

Cautela metodologica: `aid_logistics` se lee como entregas/logistica salvo que haya evidencia textual de acopio, donaciones o necesidades. `shelter_health` puede marcar salud y refugios cuando la fuente no separa ambos dominios. En personas desaparecidas, salud, refugios y conectividad se privilegia la proteccion de PII sobre cualquier union de datos.

## Resumen cuantitativo

- Fuentes consolidadas: 168.
- Relaciones posibles en matriz: 6346.
- Fuentes con mas de una funcion observable: 120.
- Fuentes con riesgo PII alto en inventario: 60.
- APIs auditadas vivas: 3 de 3; `acopiove_puntos_json` reporta 796 puntos.
- Relaciones con nota PII-safe en la matriz: 1770.

## Mapa de funciones

| Funcion | Plataformas | Riesgo PII dominante | Lectura observable |
| --- | ---: | --- | --- |
| datos/API | 82 | high | Endpoints, repositorios, datasets, dashboards o senales de datos estructurados. |
| danos | 77 | high | Reportes de danos, mapas de edificios, inspeccion estructural o senales sismicas. |
| entregas/logistica | 75 | high | Coordinacion de ayuda, trazabilidad, rutas, lotes, QR o gestion operativa. |
| personas desaparecidas | 65 | high | Busqueda, registro, localizacion o reunificacion de personas. |
| informacion verificada | 61 | high | Directorios, agregadores, recursos verificados, fuentes humanitarias o noticias. |
| refugios | 51 | high | Refugios, albergues, shelter mapping o centros de resguardo. |
| salud | 49 | high | Hospitales, pacientes, servicios medicos, insumos o apoyo psicosocial. |
| necesidades | 33 | high | Solicitudes, insumos requeridos, estados de necesidad o saturacion. |
| voluntarios | 26 | high | Voluntariado, brigadas, ayudantes o capacidades humanas coordinables. |
| acopio | 25 | low | Centros de acopio, puntos de apoyo o recepcion de suministros. |
| donaciones | 21 | low | Fondos, donantes, donaciones, campanas o canales de aporte. |
| conectividad | 19 | high | Offline-first, WiFi, mallas, BLE, comunicaciones o senal. |

## Funciones mas repetidas

- datos/API: 82 fuentes marcadas.
- danos: 77 fuentes marcadas.
- entregas/logistica: 75 fuentes marcadas.
- personas desaparecidas: 65 fuentes marcadas.
- informacion verificada: 61 fuentes marcadas.
- refugios: 51 fuentes marcadas.

Las funciones dominantes muestran mucha produccion de datos/API, logistica general, danos, personas desaparecidas e informacion verificada. La lectura operativa es fragmentacion: muchas fuentes intentan resolver funciones cercanas, pero no todas exponen campos seguros, licencia o esquema interoperable.

## Redundancias observables

La redundancia aqui significa coincidencia funcional, no duplicacion exacta de datos ni usuarios.
- danos: 9 fuentes con firma funcional similar. Ejemplos: Centinela (NUEVO); Reporta Venezuela (org) (NUEVO); RIAVE (NUEVO); SOS Venezuela (net) (NUEVO); Terremoto en Venezuela (NUEVO); Tilin App (NUEVO); Unidos Venezuela (NUEVO); Habitable (Ing. x Venezuela) (NUEVO).
- datos/API: 9 fuentes con firma funcional similar. Ejemplos: github crafter station mission ve; github cultura interactiva rva webapp; github wilterd juntosporvenezuela; 24JunVE; github carlosuriass build4venezuelarag; Build4Venezuela (Crafter Station) (TOP); github datavenezuela venezueladatacrisis; github sergioballesteros vd build4venezuelarag.
- personas desaparecidas: 9 fuentes con firma funcional similar. Ejemplos: Mascotas por Venezuela; Patas a Casa; Busqueda VZLA; Desaparecidos / Emergencia / Unif. CIVIS Venezuela; Encuentralos (tecnosoft); mBuscan; Red Sonadoras; SOS Ven (site).
- personas desaparecidas + danos: 7 fuentes con firma funcional similar. Ejemplos: Encuentralos VZLA; Huellas Can; Busqueda personas Desaparecidos Terremoto Venezuela 56.000+ reportados | 37.000+ sin contacto...; Desaparecidos Venezuela; Busqueda Tech - Apps RescataVenezuela Plataforma para busqueda y reporte de desaparecidos Act...; Terremoto Venezuela; Venezuela Reporta.
- danos + datos/API: 6 fuentes con firma funcional similar. Ejemplos: Microsoft AI for Good (HDX) (NUEVO); Sismo Venezuela; Terremoto Venezuela (app); github-takove-crisis-damage-intelligence; Busqueda Tech - Apps Juntos por Venezuela Plataforma que reune a todas las aplicaciones digit...; Reporta Venezuela (Zonas Afectadas).
- danos + informacion verificada: 4 fuentes con firma funcional similar. Ejemplos: Aid Venezuela (NUEVO); Directorio Sismo; Info Central Terremoto VE; Recursos Terremoto Venezuela.
- entregas/logistica: 4 fuentes con firma funcional similar. Ejemplos: Ayuda en Camino; Red Ayuda Venezuela; VZL Ayuda; Unificacion (Juliococo).
- personas desaparecidas + datos/API: 4 fuentes con firma funcional similar. Ejemplos: Scraper+RAG Unificado (NUEVO); Encontrados VE (Telegram); Buscador Unificado VZLA (NUEVO); Venezuela Juntos (Missing Persons Facial Recognition).

Redundancias de especial cuidado: busqueda de personas, reportes de danos y hubs multiproposito. En esos casos, unir bases por identificadores personales aumentaria riesgo; la matriz de conexiones recomienda usar agregados o claves `topic + geography + time`.

## Vacios

- Estado operativo actualizado: muchas fuentes dicen que existe un punto, mapa o app, pero pocas aportan fecha de actualizacion verificable por registro.
- Capacidad y saturacion: refugios, centros de salud y acopios aparecen como funciones, pero no siempre con capacidad, ocupacion, horario o estado operativo estructurado.
- Ciclo logistico completo: hay senales de donacion, acopio y entrega, pero falta separar promesa, stock, despacho, transito, llegada, distribucion y recepcion.
- Licencia y esquema: varias plataformas senalan API o datos, pero pocas exhiben licencia, versionado y esquema publico comparable al caso `acopiove`.
- Voluntariado agregado: hay voluntarios en descripciones y tags, pero falta una capa publica de capacidades agregadas sin datos personales.
- Conectividad operacional: aparecen WiFi, offline-first, BLE o malla, pero no siempre hay datos publicables sobre cobertura, estado de nodos o zonas sin servicio.

## Riesgos PII

- Alto riesgo: personas desaparecidas, menores, busqueda por rostro, registros de hospitales, ubicaciones exactas de personas y reportes con fotos o telefonos.
- Riesgo medio: salud, refugios, danos con foto/GPS, voluntariado individual y necesidades con texto libre.
- Riesgo variable: APIs y plataformas de conectividad; el riesgo depende del esquema, granularidad geografica, autentificacion y politicas de publicacion.
- Regla de union: no unir nombre, cedula, telefono, foto, direccion exacta ni ubicacion personal. Para analisis publico usar `topic + geography + time`, con geografia agregada y fechas redondeadas cuando aplique.

Datos que no deben interoperar en salidas publicas: registros nominales de desaparecidos, datos clinicos, fotos identificables, telefonos privados, documentos, coordenadas personales, listas de personas alojadas en refugios y disponibilidad individual de voluntarios.

## Candidatas a interoperar

Criterio inicial: senal de API o datos estructurados, funcion de datos/API, y riesgo PII distinto de alto. Esta lista es candidata tecnica, no certificacion de impacto ni aval institucional.
- github nobelaar acopio vzla: acopio|necesidades|voluntarios|danos|informacion verificada|entregas/logistica|datos/API. Riesgo depends. Senal: senal API publica.
- github globalemergency responsegrid: refugios|informacion verificada|entregas/logistica|datos/API. Riesgo depends. Senal: senal API publica.
- Terremoto VE (netlify): acopio|danos|entregas/logistica|datos/API. Riesgo depends. Senal: senal API publica.
- Venezuela Aid Finder: acopio|entregas/logistica|datos/API. Riesgo depends. Senal: senal API publica.
- Sheet Centros de Acopio (M. Lozada) (TOP): acopio|entregas/logistica|datos/API. Riesgo low. Senal: SI - Datos abiertos.
- Senal de Ayuda: conectividad|entregas/logistica|datos/API. Riesgo depends. Senal: senal API publica.
- Ayuda VE (DROSS): necesidades|entregas/logistica|datos/API. Riesgo depends. Senal: senal API publica.
- acopiove org docs api: entregas/logistica|datos/API. Riesgo depends. Senal: senal API publica.
- VZLA_DEDUP (NUEVO): informacion verificada|datos/API. Riesgo depends. Senal: SI - API abierta.
- Reporta Venezuela (Zonas Afectadas): danos|datos/API. Riesgo depends. Senal: Consume API.
- Infancia Protegida Vzla: entregas/logistica|datos/API. Riesgo low. Senal: No.
- Centraliza Ayuda Venezuela: entregas/logistica|datos/API. Riesgo low. Senal: Repo.
- github-takove-crisis-damage-intelligence: danos|datos/API. Riesgo low. Senal: senal API publica.
- github wilterd juntosporvenezuela: datos/API. Riesgo low. Senal: senal API publica.
- github sergioballesteros vd build4venezuelarag: datos/API. Riesgo depends. Senal: senal API publica.
- github cultura interactiva rva webapp: datos/API. Riesgo low. Senal: senal API publica.
- github crafter station mission ve: datos/API. Riesgo low. Senal: senal API publica.
- github carlosuriass build4venezuelarag: datos/API. Riesgo depends. Senal: senal API publica.

Integraciones recomendadas: acopios, necesidades, refugios, salud, danos y entregas solo en forma agregada por zona, tipo, estado y fecha. Las fuentes de personas desaparecidas deben interoperar, si acaso, mediante conteos, estado agregado o derivaciones controladas, no por identificadores.

## Nodos con muchas conexiones potenciales

Estos nodos aparecen con alto peso de relacion en la matriz; indican cercania funcional, no dependencia real ni impacto.
- GeoResponde: 34 conexiones con peso >= 6; suma de peso 240.
- github juanmarchetto confia: 34 conexiones con peso >= 6; suma de peso 240.
- github gaboclus ayudave: 34 conexiones con peso >= 6; suma de peso 240.
- Rastro: 34 conexiones con peso >= 6; suma de peso 240.
- github daniquishpecod4 sarab4ve: 34 conexiones con peso >= 6; suma de peso 240.
- Venezuela Response Hub: 30 conexiones con peso >= 6; suma de peso 205.
- Crisis Map: 30 conexiones con peso >= 6; suma de peso 205.
- Reencuentros Terremotos Venezuela: 30 conexiones con peso >= 6; suma de peso 205.
- ResQLink: 30 conexiones con peso >= 6; suma de peso 205.
- SismoVzla: 30 conexiones con peso >= 6; suma de peso 205.
- zerena: 30 conexiones con peso >= 6; suma de peso 205.
- Sismologia VE: 30 conexiones con peso >= 6; suma de peso 196.

## Salidas

- Matriz plataforma-funcion: `outputs/atlas/platform_function_matrix.csv`.
- Este documento: `docs/research/plans/atlas-001-ecosistema-digital.md`.

## Nota de lectura

El atlas describe que problema intenta ordenar cada herramienta segun sus senales visibles. No afirma cobertura real, uso efectivo, calidad de atencion, llegada de ayuda ni impacto social sin evidencia adicional.
