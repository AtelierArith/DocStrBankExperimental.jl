```
iscntrl(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen ein Steuerzeichen ist. Steuerzeichen sind die nicht druckbaren Zeichen des Latin-1-Teils von Unicode.

# Beispiele

```jldoctest
julia> iscntrl('\x01')
true

julia> iscntrl('a')
false
```
