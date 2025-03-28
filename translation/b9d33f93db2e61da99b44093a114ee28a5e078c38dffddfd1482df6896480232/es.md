```
Unicode.isassigned(c) -> Bool
```

Devuelve `true` si el carácter o entero dado es un punto de código Unicode asignado.

# Ejemplos

```jldoctest
julia> Unicode.isassigned(101)
true

julia> Unicode.isassigned('\x01')
true
```
