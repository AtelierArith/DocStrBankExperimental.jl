```
>(x, y)
```

Operador de comparación mayor que. Se basa en `y < x`.

# Implementación

En general, los nuevos tipos deberían implementar [`<`](@ref) en lugar de esta función, y confiar en la definición de respaldo `>(x, y) = y < x`.

# Ejemplos

```jldoctest
julia> 'a' > 'b'
false

julia> 7 > 3 > 1
true

julia> "abc" > "abd"
false

julia> 5 > 3
true
```
