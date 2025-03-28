```
skip(s, offset)
```

Buscar en un flujo relativo a la posición actual.

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang es una organización de GitHub.");

julia> seek(io, 5);

julia> skip(io, 10);

julia> read(io, Char)
'G': ASCII/Unicode U+0047 (categoría Lu: Letra, mayúscula)
```
