```
isprint(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen druckbar ist, einschließlich Leerzeichen, jedoch nicht ein Steuerzeichen.

# Beispiele

```jldoctest
julia> isprint('\x01')
false

julia> isprint('A')
true
```
