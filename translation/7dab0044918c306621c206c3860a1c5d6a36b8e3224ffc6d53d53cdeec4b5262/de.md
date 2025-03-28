```
uppercase(c::AbstractChar)
```

Konvertiere `c` in Großbuchstaben.

Siehe auch [`lowercase`](@ref), [`titlecase`](@ref).

# Beispiele

```jldoctest
julia> uppercase('a')
'A': ASCII/Unicode U+0041 (Kategorie Lu: Buchstabe, Großbuchstabe)

julia> uppercase('ê')
'Ê': Unicode U+00CA (Kategorie Lu: Buchstabe, Großbuchstabe)
```
