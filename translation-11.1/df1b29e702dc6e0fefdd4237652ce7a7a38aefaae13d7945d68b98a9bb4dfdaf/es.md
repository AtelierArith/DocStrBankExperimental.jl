```
arg_read(f::Function, arg::ArgRead) -> f(arg_io)
```

La función `arg_read` acepta un argumento `arg` que puede ser cualquiera de estos:

  * `AbstractString`: una ruta de archivo que se abrirá para lectura
  * `AbstractCmd`: un comando que se ejecutará, leyendo desde su salida estándar
  * `IO`: un manejador de IO abierto del que se leerá

Ya sea que el cuerpo devuelva normalmente o lance un error, una ruta que se abra se cerrará antes de devolver de `arg_read` y un manejador de `IO` se vaciará pero no se cerrará antes de devolver de `arg_read`.

Nota: al abrir un archivo, ArgTools pasará `lock = false` a la llamada de archivo `open(...)`. Por lo tanto, el objeto devuelto por esta función no debe ser utilizado desde múltiples hilos. Esta restricción puede relajarse en el futuro, lo que no rompería ningún código funcional.
