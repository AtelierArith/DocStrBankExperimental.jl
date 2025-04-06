```
seekstart(s)
```

Bewege einen Stream zu seinem Anfang.

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (Kategorie Lu: Buchstabe, Großbuchstabe)

julia> seekstart(io);

julia> read(io, Char)
'J': ASCII/Unicode U+004A (Kategorie Lu: Buchstabe, Großbuchstabe)
```
