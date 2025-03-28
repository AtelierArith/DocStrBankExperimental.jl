```
open(command, mode::AbstractString, stdio=devnull)
```

Ejecuta `command` de manera asíncrona. Al igual que `open(command, stdio; read, write)`, excepto que se especifican las banderas de lectura y escritura a través de una cadena de modo en lugar de argumentos de palabra clave. Las cadenas de modo posibles son:

| Modo | Descripción    | Palabras clave              |
|:---- |:-------------- |:--------------------------- |
| `r`  | leer           | ninguna                     |
| `w`  | escribir       | `write = true`              |
| `r+` | leer, escribir | `read = true, write = true` |
| `w+` | leer, escribir | `read = true, write = true` |
