```
isodd(x::Number) -> Bool
```

Devuelve `true` si `x` es un entero impar (es decir, un entero no divisible por 2), y `false` en caso contrario.

!!! compat "Julia 1.7"
    Los argumentos no `Integer` requieren Julia 1.7 o posterior.


# Ejemplos

```jldoctest
julia> isodd(9)
true

julia> isodd(10)
false
```
