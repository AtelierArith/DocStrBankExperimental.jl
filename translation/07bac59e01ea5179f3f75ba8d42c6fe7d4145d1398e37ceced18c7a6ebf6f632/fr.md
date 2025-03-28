```
first(coll)
```

Obtenez le premier élément d'une collection itérable. Retournez le point de départ d'un [`AbstractRange`](@ref) même s'il est vide.

Voir aussi : [`only`](@ref), [`firstindex`](@ref), [`last`](@ref).

# Exemples

```jldoctest
julia> first(2:2:10)
2

julia> first([1; 2; 3; 4])
1
```
