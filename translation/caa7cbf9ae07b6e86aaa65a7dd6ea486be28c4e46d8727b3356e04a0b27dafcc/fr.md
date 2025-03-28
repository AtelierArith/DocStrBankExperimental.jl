```
opnorm(A::AbstractMatrix, p::Real=2)
```

Calculez la norme opérateur (ou norme de matrice) induite par la norme vectorielle `p`, où les valeurs valides de `p` sont `1`, `2` ou `Inf`. (Notez que pour les matrices creuses, `p=2` n'est actuellement pas implémenté.) Utilisez [`norm`](@ref) pour calculer la norme de Frobenius.

Lorsque `p=1`, la norme opérateur est la somme maximale des valeurs absolues des colonnes de `A` :

$$
\|A\|_1 = \max_{1 ≤ j ≤ n} \sum_{i=1}^m | a_{ij} |
$$

avec $a_{ij}$ les éléments de $A$, et $m$ et $n$ ses dimensions.

Lorsque `p=2`, la norme opérateur est la norme spectrale, égale à la plus grande valeur singulière de `A`.

Lorsque `p=Inf`, la norme opérateur est la somme maximale des valeurs absolues des lignes de `A` :

$$
\|A\|_\infty = \max_{1 ≤ i ≤ m} \sum _{j=1}^n | a_{ij} |
$$

# Exemples

```jldoctest
julia> A = [1 -2 -3; 2 3 -1]
2×3 Matrix{Int64}:
 1  -2  -3
 2   3  -1

julia> opnorm(A, Inf)
6.0

julia> opnorm(A, 1)
5.0
```
