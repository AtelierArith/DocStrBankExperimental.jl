```
isreadonly(io) -> Bool
```

Determina si un flujo es de solo lectura.

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang es una organización de GitHub");

julia> isreadonly(io)
true

julia> io = IOBuffer();

julia> isreadonly(io)
false
```
