```
eigen(A, B; sortby) -> GeneralizedEigen
```

Calcule la décomposition des valeurs propres généralisées de `A` et `B`, retournant un objet de factorisation [`GeneralizedEigen`](@ref) `F` qui contient les valeurs propres généralisées dans `F.values` et les vecteurs propres généralisés dans les colonnes de la matrice `F.vectors`. Cela correspond à la résolution d'un problème de valeurs propres généralisées de la forme `Ax =  λBx`, où `A, B` sont des matrices, `x` est un vecteur propre, et `λ` est une valeur propre. (Le `k`-ième vecteur propre généralisé peut être obtenu à partir de la tranche `F.vectors[:, k]`.)

L'itération de la décomposition produit les composants `F.values` et `F.vectors`.

Par défaut, les valeurs propres et les vecteurs sont triés lexicographiquement par `(real(λ),imag(λ))`. Une fonction de comparaison différente `by(λ)` peut être passée à `sortby`, ou vous pouvez passer `sortby=nothing` pour laisser les valeurs propres dans un ordre arbitraire.

# Exemples

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B);

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
