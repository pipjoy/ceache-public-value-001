# Data Safety

Este repositorio esta disenado para compartir conocimiento operativo sin exponer personas.

## Datos permitidos

Se pueden compartir datos agregados y operativos:

- categoria de necesidad;
- cantidad y unidad;
- estado operativo;
- zona agregada;
- fecha de actualizacion;
- fuente;
- permiso o licencia;
- etapa de entrega;
- capacidad agregada;
- restricciones operativas.

## Datos no permitidos

No se deben enviar ni publicar:

- nombres de personas vulnerables;
- cedulas o documentos;
- telefonos privados;
- direcciones exactas;
- ubicaciones sensibles;
- datos de menores;
- salud individual;
- listas nominales de personas alojadas;
- personas desaparecidas;
- fotos identificables;
- chats privados;
- rutas vulnerables;
- texto libre con informacion personal.

## Regla central

```text
Interoperar funciones, no personas.
```

## Riesgo por combinacion

Un campo puede parecer seguro de forma aislada y volverse sensible al combinarse con otros.

Ejemplo:

```text
zona + fecha + categoria + cantidad + fuente + estado
```

Por eso toda publicacion debe revisar riesgo de reidentificacion antes de abrir datos.

