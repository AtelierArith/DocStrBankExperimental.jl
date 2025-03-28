```
open(filename::AbstractString; lock = true, keywords...) -> IOStream
```

Abre un archivo en un modo especificado por cinco argumentos booleanos de palabra clave:

| Palabra clave | Descripción           | Predeterminado                        |
|:------------- |:--------------------- |:------------------------------------- |
| `read`        | abrir para lectura    | `!write`                              |
| `write`       | abrir para escritura  | `truncate \| append`                  |
| `create`      | crear si no existe    | `!read & write \| truncate \| append` |
| `truncate`    | truncar a tamaño cero | `!read & write`                       |
| `append`      | buscar al final       | `false`                               |

El predeterminado cuando no se pasan palabras clave es abrir archivos solo para lectura. Devuelve un flujo para acceder al archivo abierto.

El argumento de palabra clave `lock` controla si las operaciones estarán bloqueadas para un acceso seguro en múltiples hilos.

!!! compat "Julia 1.5"
    El argumento `lock` está disponible a partir de Julia 1.5.

