```
isxdigit(c::AbstractChar) -> Bool
```

Überprüfen, ob ein Zeichen eine gültige hexadezimale Ziffer ist. Beachten Sie, dass `x` (wie im Standardpräfix `0x`) nicht eingeschlossen ist.

# Beispiele

```jldoctest
julia> isxdigit('a')
true

julia> isxdigit('x')
false
```
