```
iseven(x::Number) -> Bool
```

Devuelve `true` si `x` es un entero par (es decir, un entero divisible por 2), y `false` en caso contrario.

!!! compat "Julia 1.7"
    Los argumentos no `Integer` requieren Julia 1.7 o posterior.


# Ejemplos

```jldoctest
julia> iseven(9)
false

julia> iseven(10)
true
```
