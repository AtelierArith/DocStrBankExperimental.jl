```
skip(s, offset)
```

Chercher un flux par rapport à la position actuelle.

# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang est une organisation GitHub.");

julia> seek(io, 5);

julia> skip(io, 10);

julia> read(io, Char)
'G': ASCII/Unicode U+0047 (catégorie Lu : Lettre, majuscule)
```
