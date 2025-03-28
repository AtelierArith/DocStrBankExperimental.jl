```
skip(s, offset)
```

Suchen Sie einen Stream relativ zur aktuellen Position.

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.");

julia> seek(io, 5);

julia> skip(io, 10);

julia> read(io, Char)
'G': ASCII/Unicode U+0047 (Kategorie Lu: Buchstabe, Großbuchstabe)
```
