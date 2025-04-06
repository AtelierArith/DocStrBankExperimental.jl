```
deleteat!(a::Vector, i::Integer)
```

Supprime l'élément à l'index `i` donné et retourne le `a` modifié. Les éléments suivants sont décalés pour combler le vide résultant.

Voir aussi : [`keepat!`](@ref), [`delete!`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Exemples

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 2)
5-element Vector{Int64}:
 6
 4
 3
 2
 1
```
