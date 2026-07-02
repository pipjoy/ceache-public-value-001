# Checklist de calidad para datos operativos

Johaina Chavez, Data Scientist  
Ceache Lab  
Version: 0.1.1  
Fecha: 2026-07-02

Usa esta checklist antes de compartir una hoja, lista, formulario, app o API.

## 1. Seguridad

- [ ] La hoja no contiene cedulas, documentos ni pasaportes.
- [ ] La hoja no contiene telefonos privados.
- [ ] La hoja no contiene direcciones exactas de personas vulnerables.
- [ ] La hoja no contiene nombres de personas afectadas.
- [ ] La hoja no contiene salud individual.
- [ ] La hoja no contiene informacion de menores.
- [ ] La hoja no contiene chats privados completos.
- [ ] La hoja no contiene fotos o enlaces que identifiquen personas.

## 2. Utilidad

- [ ] Cada fila representa una observacion, pedido, oferta, punto, entrega o fuente.
- [ ] Existe una columna de categoria.
- [ ] Existe una columna de cantidad.
- [ ] Existe una columna de unidad.
- [ ] Existe una columna de zona agregada.
- [ ] Existe una columna de estado.
- [ ] Existe una columna de fecha observada o fecha de actualizacion.
- [ ] Existe una columna de fuente.

## 3. Trazabilidad

- [ ] Se puede saber quien produjo o reporto el dato a nivel institucional o comunitario.
- [ ] Se puede saber cuando fue actualizado por ultima vez.
- [ ] Se distingue entre dato reportado, verificado, en proceso, entregado y cerrado.
- [ ] Se indica si la fuente permite analisis interno.
- [ ] Se indica si la fuente permite publicacion agregada.

## 4. Comparabilidad

- [ ] Las categorias usan nombres consistentes.
- [ ] Las unidades son comparables: kg, litros, cajas, unidades, personas, cupos.
- [ ] Las zonas usan una convencion estable.
- [ ] Los estados usan valores consistentes.
- [ ] Las fechas tienen formato ISO recomendado: YYYY-MM-DD.

## 5. Antes de publicar

- [ ] El dato puede agregarse sin identificar personas.
- [ ] El dato no revela rutas sensibles.
- [ ] El dato no expone refugios vulnerables sin permiso.
- [ ] El dato no permite inferir ubicacion exacta de una persona.
- [ ] El dato no mezcla contexto sensible dentro de texto libre.

## Decision

Si una hoja falla en seguridad, no debe publicarse.

Si una hoja falla en utilidad, puede limpiarse.

Si una hoja falla en trazabilidad, debe marcarse como preliminar.

Si una hoja falla en comparabilidad, puede mapearse con `field_mapping_template.csv`.
