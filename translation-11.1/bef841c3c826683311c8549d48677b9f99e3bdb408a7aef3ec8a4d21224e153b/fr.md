```
Base.split_rest(collection, n::Int[, itr_state]) -> (rest_but_n, last_n)
```

Fonction générique pour diviser la queue de `collection`, à partir d'un état d'itération spécifique `itr_state`. Renvoie un tuple de deux nouvelles collections. La première contient tous les éléments de la queue sauf les `n` derniers, qui constituent la deuxième collection.

Le type de la première collection suit généralement celui de [`Base.rest`](@ref), sauf que le cas de repli n'est pas paresseux, mais est collecté de manière proactive dans un vecteur.

Peut être surchargé pour des types de collection définis par l'utilisateur afin de personnaliser le comportement de [l'absorption dans les affectations](@ref destructuring-assignment) en position non finale, comme `a, b..., c = collection`.

!!! compat "Julia 1.9"
    `Base.split_rest` nécessite au moins Julia 1.9.


Voir aussi : [`Base.rest`](@ref).

# Exemples

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.split_rest(a, 1, state)
(1, ([3, 2], [4]))
```
