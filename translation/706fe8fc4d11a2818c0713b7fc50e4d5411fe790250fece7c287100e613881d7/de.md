```
seek(s, pos)
```

Suchen Sie einen Stream an die angegebene Position.

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (Kategorie Lu: Buchstabe, Großbuchstabe)
```
