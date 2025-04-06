```
seek(s, pos)
```

Buscar un flujo en la posición dada.

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang es una organización de GitHub.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (categoría Lu: Letra, mayúscula)
```
