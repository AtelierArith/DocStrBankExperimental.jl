```
isspace(c::AbstractChar) -> Bool
```

Prueba si un carácter es cualquier carácter de espacio en blanco. Incluye caracteres ASCII '\t', '\n', '\v', '\f', '\r' y ' ', el carácter Latin-1 U+0085, y caracteres en la categoría Unicode Zs.

# Ejemplos

```jldoctest
julia> isspace('\n')
true

julia> isspace('\r')
true

julia> isspace(' ')
true

julia> isspace('\x20')
true
```
