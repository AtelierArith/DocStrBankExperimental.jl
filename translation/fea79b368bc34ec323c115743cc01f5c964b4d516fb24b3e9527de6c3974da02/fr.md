```
push!(collection, items...) -> collection
```

Insérer un ou plusieurs `items` dans `collection`. Si `collection` est un conteneur ordonné, les éléments sont insérés à la fin (dans l'ordre donné).

# Exemples

```jldoctest
julia> push!([1, 2, 3], 4, 5, 6)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

Si `collection` est ordonné, utilisez [`append!`](@ref) pour ajouter tous les éléments d'un autre conteneur. Le résultat de l'exemple précédent est équivalent à `append!([1, 2, 3], [4, 5, 6])`. Pour les objets `AbstractSet`, [`union!`](@ref) peut être utilisé à la place.

Voir [`sizehint!`](@ref) pour des notes sur le modèle de performance.

Voir aussi [`pushfirst!`](@ref).
