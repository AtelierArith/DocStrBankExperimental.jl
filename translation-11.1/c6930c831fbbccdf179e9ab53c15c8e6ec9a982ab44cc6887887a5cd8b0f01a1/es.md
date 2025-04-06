```
nextprod(factors::Union{Tuple,AbstractVector}, n)
```

Siguiente entero mayor o igual a `n` que se puede escribir como $\prod k_i^{p_i}$ para enteros $p_1$, $p_2$, etcétera, para factores $k_i$ en `factors`.

# Ejemplos

```jldoctest
julia> nextprod((2, 3), 105)
108

julia> 2^2 * 3^3
108
```

!!! compat "Julia 1.6"
    El método que acepta una tupla requiere Julia 1.6 o posterior.

