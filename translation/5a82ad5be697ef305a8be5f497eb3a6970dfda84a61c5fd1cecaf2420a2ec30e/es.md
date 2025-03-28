```
seekstart(s)
```

Busca un flujo hasta su comienzo.

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (categoría Lu: Letra, mayúscula)

julia> seekstart(io);

julia> read(io, Char)
'J': ASCII/Unicode U+004A (categoría Lu: Letra, mayúscula)
```
