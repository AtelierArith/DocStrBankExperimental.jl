```
norm(A, p::Real=2)
```

Pour tout conteneur itérable `A` (y compris les tableaux de n'importe quelle dimension) de nombres (ou tout type d'élément pour lequel `norm` est défini), calculez la `p`-norme (par défaut `p=2`) comme si `A` était un vecteur de la longueur correspondante.

La `p`-norme est définie comme

$$
\|A\|_p = \left( \sum_{i=1}^n | a_i | ^p \right)^{1/p}
$$

avec $a_i$ les entrées de `A`, $| a_i |$ la [`norm`](@ref) de $a_i$, et $n$ la longueur de `A`. Puisque la `p`-norme est calculée en utilisant les [`norm`](@ref)s des entrées de `A`, la `p`-norme d'un vecteur de vecteurs n'est pas compatible avec l'interprétation de celui-ci comme un vecteur bloc en général si `p != 2`.

`p` peut prendre n'importe quelle valeur numérique (bien que toutes les valeurs ne produisent pas une norme vectorielle mathématiquement valide). En particulier, `norm(A, Inf)` renvoie la plus grande valeur dans `abs.(A)`, tandis que `norm(A, -Inf)` renvoie la plus petite. Si `A` est une matrice et `p=2`, alors cela équivaut à la norme de Frobenius.

Le deuxième argument `p` n'est pas nécessairement une partie de l'interface pour `norm`, c'est-à-dire qu'un type personnalisé peut n'implémenter que `norm(A)` sans deuxième argument.

Utilisez [`opnorm`](@ref) pour calculer la norme opérateur d'une matrice.

# Exemples

```jldoctest
julia> v = [3, -2, 6]
3-element Vector{Int64}:
  3
 -2
  6

julia> norm(v)
7.0

julia> norm(v, 1)
11.0

julia> norm(v, Inf)
6.0

julia> norm([1 2 3; 4 5 6; 7 8 9])
16.881943016134134

julia> norm([1 2 3 4 5 6 7 8 9])
16.881943016134134

julia> norm(1:9)
16.881943016134134

julia> norm(hcat(v,v), 1) == norm(vcat(v,v), 1) != norm([v,v], 1)
true

julia> norm(hcat(v,v), 2) == norm(vcat(v,v), 2) == norm([v,v], 2)
true

julia> norm(hcat(v,v), Inf) == norm(vcat(v,v), Inf) != norm([v,v], Inf)
true
```
