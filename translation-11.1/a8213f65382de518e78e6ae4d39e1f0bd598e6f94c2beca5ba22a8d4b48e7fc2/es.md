```
LogRecord
```

Almacena los resultados de un solo evento de registro. Campos:

  * `level`: el [`LogLevel`](@ref) del mensaje de registro
  * `message`: el contenido textual del mensaje de registro
  * `_module`: el módulo del evento de registro
  * `group`: el grupo de registro (por defecto, el nombre del archivo que contiene el evento de registro)
  * `id`: el ID del evento de registro
  * `file`: el archivo que contiene el evento de registro
  * `line`: la línea dentro del archivo del evento de registro
  * `kwargs`: cualquier argumento de palabra clave pasado al evento de registro
