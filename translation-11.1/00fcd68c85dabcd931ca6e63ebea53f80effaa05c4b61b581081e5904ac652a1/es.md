```
strptime([formato], timestr)
```

Analiza una cadena de tiempo formateada en un `TmStruct` que da los segundos, minutos, horas, fecha, etc. Los formatos admitidos son los mismos que los de la biblioteca estándar de C. En algunas plataformas, las zonas horarias no se analizarán correctamente. Si el resultado de esta función se pasará a `time` para convertirlo en segundos desde la época, el campo `isdst` debe llenarse manualmente. Establecerlo en `-1` indicará a la biblioteca C que use la configuración del sistema actual para determinar la zona horaria.
