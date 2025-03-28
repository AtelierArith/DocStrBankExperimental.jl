```
isletter(c::AbstractChar) -> Bool
```

Überprüfen, ob ein Zeichen ein Buchstabe ist. Ein Zeichen wird als Buchstabe klassifiziert, wenn es zur Unicode-Allgemeinkategorie Buchstabe gehört, d.h. ein Zeichen, dessen Kategorienummer mit 'L' beginnt.

Siehe auch: [`isdigit`](@ref).

# Beispiele

```jldoctest
julia> isletter('❤')
false

julia> isletter('α')
true

julia> isletter('9')
false
```
