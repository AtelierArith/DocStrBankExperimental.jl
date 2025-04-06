```
titlecase(c::AbstractChar)
```

Konvertiere `c` in Titelcase. Dies kann sich von Großbuchstaben für Digraphen unterscheiden, vergleiche das Beispiel unten.

Siehe auch [`uppercase`](@ref), [`lowercase`](@ref).

# Beispiele

```jldoctest
julia> titlecase('a')
'A': ASCII/Unicode U+0041 (Kategorie Lu: Buchstabe, Großbuchstabe)

julia> titlecase('ǆ')
'ǅ': Unicode U+01C5 (Kategorie Lt: Buchstabe, Titelcase)

julia> uppercase('ǆ')
'Ǆ': Unicode U+01C4 (Kategorie Lu: Buchstabe, Großbuchstabe)
```
