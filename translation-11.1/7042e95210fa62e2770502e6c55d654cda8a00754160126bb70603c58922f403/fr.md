```
length(collection) -> Integer
```

Retourne le nombre d'éléments dans la collection.

Utilisez [`lastindex`](@ref) pour obtenir le dernier index valide d'une collection indexable.

Voir aussi : [`size`](@ref), [`ndims`](@ref), [`eachindex`](@ref).

# Exemples

```jldoctest
julia> length(1:5)
5

julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
