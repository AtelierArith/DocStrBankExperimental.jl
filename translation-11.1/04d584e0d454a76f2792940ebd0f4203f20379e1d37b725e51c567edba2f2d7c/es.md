```
open(filename::AbstractString, [mode::AbstractString]; lock = true) -> IOStream
```

Sintaxis alternativa para open, donde se utiliza un especificador de modo basado en cadenas en lugar de los cinco booleanos. Los valores de `mode` corresponden a los de `fopen(3)` o Perl `open`, y son equivalentes a establecer los siguientes grupos booleanos:

| Modo | Descripción                    | Palabras clave                 |
|:---- |:------------------------------ |:------------------------------ |
| `r`  | leer                           | ninguno                        |
| `w`  | escribir, crear, truncar       | `write = true`                 |
| `a`  | escribir, crear, agregar       | `append = true`                |
| `r+` | leer, escribir                 | `read = true, write = true`    |
| `w+` | leer, escribir, crear, truncar | `truncate = true, read = true` |
| `a+` | leer, escribir, crear, agregar | `append = true, read = true`   |

El argumento de palabra clave `lock` controla si las operaciones estarán bloqueadas para un acceso seguro en múltiples hilos.

# Ejemplos

```jldoctest
julia> io = open("myfile.txt", "w");

julia> write(io, "¡Hola mundo!");

julia> close(io);

julia> io = open("myfile.txt", "r");

julia> read(io, String)
"¡Hola mundo!"

julia> write(io, "Este archivo es solo de lectura")
ERROR: ArgumentError: write failed, IOStream is not writeable
[...]

julia> close(io)

julia> io = open("myfile.txt", "a");

julia> write(io, "Este flujo no es solo de lectura")
28

julia> close(io)

julia> rm("myfile.txt")
```

!!! compat "Julia 1.5"
    El argumento `lock` está disponible a partir de Julia 1.5.

