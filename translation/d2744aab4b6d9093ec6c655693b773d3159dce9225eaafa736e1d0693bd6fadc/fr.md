```
keepat!(a::Vector, inds)
keepat!(a::BitVector, inds)
```

Supprime les éléments à tous les indices qui ne sont pas donnés par `inds`, et retourne le `a` modifié. Les éléments qui sont conservés sont décalés pour remplir les espaces résultants.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


`inds` doit être un itérateur d'indices entiers triés et uniques. Voir aussi [`deleteat!`](@ref).

!!! compat "Julia 1.7"
    Cette fonction est disponible depuis Julia 1.7.


# Exemples

```jldoctest
julia> keepat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 6
 4
 2
```
