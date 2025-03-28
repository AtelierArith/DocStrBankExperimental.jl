```
cumsum(itr)
```

Suma acumulativa de un iterador.

Véase también [`accumulate`](@ref) para aplicar funciones distintas de `+`.

!!! compat "Julia 1.5"
    `cumsum` en un iterador que no es un arreglo requiere al menos Julia 1.5.


# Ejemplos

```jldoctest
julia> cumsum(1:3)
3-element Vector{Int64}:
 1
 3
 6

julia> cumsum((true, false, true, false, true))
(1, 1, 2, 2, 3)

julia> cumsum(fill(1, 2) for i in 1:3)
3-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]
 [3, 3]
```
