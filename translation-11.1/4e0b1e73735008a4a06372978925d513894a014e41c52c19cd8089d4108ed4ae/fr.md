```
append!(collection, collections...) -> collection.
```

Pour un conteneur ordonné `collection`, ajoutez les éléments de chaque `collections` à la fin de celui-ci.

!!! compat "Julia 1.6"
    Spécifier plusieurs collections à ajouter nécessite au moins Julia 1.6.


# Exemples

```jldoctest
julia> append!([1], [2, 3])
3-element Vector{Int64}:
 1
 2
 3

julia> append!([1, 2, 3], [4, 5], [6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

Utilisez [`push!`](@ref) pour ajouter des éléments individuels à `collection` qui ne sont pas déjà dans une autre collection. Le résultat de l'exemple précédent est équivalent à `push!([1, 2, 3], 4, 5, 6)`.

Voir [`sizehint!`](@ref) pour des notes sur le modèle de performance.

Voir aussi [`vcat`](@ref) pour les vecteurs, [`union!`](@ref) pour les ensembles, et [`prepend!`](@ref) et [`pushfirst!`](@ref) pour l'ordre opposé.
