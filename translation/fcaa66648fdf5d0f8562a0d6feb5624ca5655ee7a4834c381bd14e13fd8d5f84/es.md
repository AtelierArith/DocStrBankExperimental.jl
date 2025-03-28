```
open(f::Function, args...; kwargs...)
```

Aplica la función `f` al resultado de `open(args...; kwargs...)` y cierra el descriptor de archivo resultante al finalizar.

# Ejemplos

```jldoctest
julia> write("myfile.txt", "¡Hola mundo!");

julia> open(io->read(io, String), "myfile.txt")
"¡Hola mundo!"

julia> rm("myfile.txt")
```
