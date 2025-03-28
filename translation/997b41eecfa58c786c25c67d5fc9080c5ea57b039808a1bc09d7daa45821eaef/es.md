```
setdiff(s, itrs...)
```

Construye el conjunto de elementos en `s` pero no en ninguno de los iterables en `itrs`. Mantiene el orden con arreglos.

Véase también [`setdiff!`](@ref), [`union`](@ref) y [`intersect`](@ref).

# Ejemplos

```jldoctest
julia> setdiff([1,2,3], [3,4,5])
2-element Vector{Int64}:
 1
 2
```
