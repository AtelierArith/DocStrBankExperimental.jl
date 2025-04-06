```
isnumeric(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen numerisch ist. Ein Zeichen wird als numerisch klassifiziert, wenn es zur Unicode-Allgemeinkategorie Zahl gehört, d.h. ein Zeichen, dessen Kategorienummer mit 'N' beginnt.

Beachten Sie, dass diese breite Kategorie Zeichen wie ¾ und ௰ umfasst. Verwenden Sie [`isdigit`](@ref), um zu überprüfen, ob ein Zeichen eine Dezimalziffer zwischen 0 und 9 ist.

# Beispiele

```jldoctest
julia> isnumeric('௰')
true

julia> isnumeric('9')
true

julia> isnumeric('α')
false

julia> isnumeric('❤')
false
```
