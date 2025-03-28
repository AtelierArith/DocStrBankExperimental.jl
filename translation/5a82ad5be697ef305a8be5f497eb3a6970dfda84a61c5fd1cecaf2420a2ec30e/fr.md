```
seekstart(s)
```

Déplace un flux au début.

# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang est une organisation GitHub.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (catégorie Lu: Lettre, majuscule)

julia> seekstart(io);

julia> read(io, Char)
'J': ASCII/Unicode U+004A (catégorie Lu: Lettre, majuscule)
```
