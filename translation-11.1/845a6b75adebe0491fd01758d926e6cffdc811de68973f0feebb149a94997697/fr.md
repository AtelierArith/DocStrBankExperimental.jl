```
filter(f)
```

Créez une fonction qui filtre ses arguments avec la fonction `f` en utilisant [`filter`](@ref), c'est-à-dire une fonction équivalente à `x -> filter(f, x)`.

La fonction retournée est de type `Base.Fix1{typeof(filter)}`, qui peut être utilisée pour implémenter des méthodes spécialisées.

# Exemples

```jldoctest
julia> (1, 2, Inf, 4, NaN, 6) |> filter(isfinite)
(1, 2, 4, 6)

julia> map(filter(iseven), [1:3, 2:4, 3:5])
3-element Vector{Vector{Int64}}:
 [2]
 [2, 4]
 [4]
```

!!! compat "Julia 1.9"
    Cette méthode nécessite au moins Julia 1.9.

