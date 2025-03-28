```
iscntrl(c::AbstractChar) -> Bool
```

Prueba si un carácter es un carácter de control. Los caracteres de control son los caracteres no imprimibles del subconjunto Latin-1 de Unicode.

# Ejemplos

```jldoctest
julia> iscntrl('\x01')
true

julia> iscntrl('a')
false
```
