```
arg_write(f::Function, arg::ArgWrite) -> arg
arg_write(f::Function, arg::Nothing) -> tempname()
```

La función `arg_read` acepta un argumento `arg` que puede ser cualquiera de estos:

  * `AbstractString`: una ruta de archivo que se abrirá para escritura
  * `AbstractCmd`: un comando que se ejecutará, escribiendo en su entrada estándar
  * `IO`: un manejador de IO abierto al que se escribirá
  * `Nothing`: se debe escribir en una ruta temporal

Si el cuerpo retorna normalmente, una ruta que está abierta se cerrará al completarse; un argumento de manejador de IO se deja abierto pero se vacía antes de retornar. Si el argumento es `nothing`, entonces se abre una ruta temporal para escritura y se cierra al completarse, y la ruta se devuelve desde `arg_write`. En todos los demás casos, se devuelve el propio `arg`. Este es un patrón útil ya que puedes devolver consistentemente lo que se escribió, ya sea que se haya pasado un argumento o no.

Si hay un error durante la evaluación del cuerpo, una ruta que se abrió con `arg_write` para escritura será eliminada, ya sea que se pase como una cadena o como una ruta temporal generada cuando `arg` es `nothing`.

Nota: al abrir un archivo, ArgTools pasará `lock = false` a la llamada de archivo `open(...)`. Por lo tanto, el objeto devuelto por esta función no debe ser utilizado desde múltiples hilos. Esta restricción puede ser relajada en el futuro, lo que no rompería ningún código funcional.
