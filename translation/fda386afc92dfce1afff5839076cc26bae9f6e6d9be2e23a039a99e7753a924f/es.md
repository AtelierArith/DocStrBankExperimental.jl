```
Base64EncodePipe(ostream)
```

Devuelve un nuevo flujo de E/S de solo escritura, que convierte cualquier byte escrito en él en bytes ASCII codificados en base64 escritos en `ostream`. Llamar a [`close`](@ref) en el flujo `Base64EncodePipe` es necesario para completar la codificación (pero no cierra `ostream`).

# Ejemplos

```jldoctest
julia> io = IOBuffer();

julia> iob64_encode = Base64EncodePipe(io);

julia> write(iob64_encode, "Hello!")
6

julia> close(iob64_encode);

julia> str = String(take!(io))
"SGVsbG8h"

julia> String(base64decode(str))
"Hello!"
```
