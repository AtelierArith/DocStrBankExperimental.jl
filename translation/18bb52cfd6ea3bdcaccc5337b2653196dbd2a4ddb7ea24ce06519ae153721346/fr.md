```
keys(a::AbstractArray)
```

Renvoie un tableau efficace décrivant tous les indices valides pour `a` disposés dans la forme de `a` lui-même.

Les clés des tableaux unidimensionnels (vecteurs) sont des entiers, tandis que tous les autres tableaux N-dimensionnels utilisent [`CartesianIndex`](@ref) pour décrire leurs emplacements. Souvent, les types de tableaux spéciaux [`LinearIndices`](@ref) et [`CartesianIndices`](@ref) sont utilisés pour représenter efficacement ces tableaux d'entiers et de `CartesianIndex`, respectivement.

Notez que les `keys` d'un tableau peuvent ne pas être le type d'index le plus efficace ; pour des performances maximales, utilisez plutôt [`eachindex`](@ref).

# Exemples

```jldoctest
julia> keys([4, 5, 6])
3-element LinearIndices{1, Tuple{Base.OneTo{Int64}}}:
 1
 2
 3

julia> keys([4 5; 6 7])
CartesianIndices((2, 2))
```
