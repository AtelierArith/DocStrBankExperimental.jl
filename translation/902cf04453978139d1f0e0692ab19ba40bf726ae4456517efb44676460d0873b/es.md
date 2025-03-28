```
exp2(x)
```

Calcula la exponencial de base 2 de `x`, en otras palabras $2^x$.

Véase también [`ldexp`](@ref), [`<<`](@ref).

# Ejemplos

```jldoctest
julia> exp2(5)
32.0

julia> 2^5
32

julia> exp2(63) > typemax(Int)
true
```
