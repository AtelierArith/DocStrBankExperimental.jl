```
product(iters...)
```

Renvoie un itérateur sur le produit de plusieurs itérateurs. Chaque élément généré est un tuple dont l'élément `i` vient de l'itérateur d'argument `i`. Le premier itérateur change le plus rapidement.

Voir aussi : [`zip`](@ref), [`Iterators.flatten`](@ref).

# Exemples

```jldoctest
julia> collect(Iterators.product(1:2, 3:5))
2×3 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (1, 4)  (1, 5)
 (2, 3)  (2, 4)  (2, 5)

julia> ans == [(x,y) for x in 1:2, y in 3:5]  # collecte un générateur impliquant Iterators.product
true
```
