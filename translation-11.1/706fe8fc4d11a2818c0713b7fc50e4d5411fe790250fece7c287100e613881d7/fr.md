```
seek(s, pos)
```

Cherchez un flux à la position donnée.

# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang est une organisation GitHub.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (catégorie Lu: Lettre, majuscule)
```
