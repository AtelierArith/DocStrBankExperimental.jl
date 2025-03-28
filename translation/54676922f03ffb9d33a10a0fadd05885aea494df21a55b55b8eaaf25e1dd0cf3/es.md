```
ConsoleLogger([stream,] min_level=Info; meta_formatter=default_metafmt,
              show_limited=true, right_justify=0)
```

Registrador con formato optimizado para la legibilidad en una consola de texto, por ejemplo, trabajo interactivo con el REPL de Julia.

Los niveles de registro inferiores a `min_level` son filtrados.

El formato del mensaje se puede controlar configurando argumentos de palabra clave:

  * `meta_formatter` es una función que toma los metadatos del evento de registro `(nivel, _módulo, grupo, id, archivo, línea)` y devuelve un color (como se pasaría a printstyled), un prefijo y un sufijo para el mensaje de registro.  El valor predeterminado es prefijar con el nivel de registro y un sufijo que contenga el módulo, el archivo y la ubicación de la línea.
  * `show_limited` limita la impresión de estructuras de datos grandes a algo que puede caber en la pantalla configurando la clave `:limit` de `IOContext` durante el formato.
  * `right_justify` es la columna entera en la que los metadatos del registro están justificados a la derecha. El valor predeterminado es cero (los metadatos van en su propia línea).
