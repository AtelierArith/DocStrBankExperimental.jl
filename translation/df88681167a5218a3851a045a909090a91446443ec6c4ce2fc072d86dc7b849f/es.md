```
symdiff(s, itrs...)
```

Construye la diferencia simétrica de los elementos en los conjuntos pasados. Cuando `s` no es un `AbstractSet`, se mantiene el orden.

Véase también [`symdiff!`](@ref), [`setdiff`](@ref), [`union`](@ref) y [`intersect`](@ref).

# Ejemplos

```jldoctest
julia> symdiff([1,2,3], [3,4,5], [4,5,6])
3-element Vector{Int64}:
 1
 2
 6

julia> symdiff([1,2,1], [2, 1, 2])
Int64[]
```
