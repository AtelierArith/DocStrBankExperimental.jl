```
isprint(c::AbstractChar) -> Bool
```

Prueba si un carácter es imprimible, incluyendo espacios, pero no un carácter de control.

# Ejemplos

```jldoctest
julia> isprint('\x01')
false

julia> isprint('A')
true
```
