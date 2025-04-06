```
GeneralizedEigen <: Factorization
```

Type de factorisation matricielle de la décomposition généralisée des valeurs propres/spectrales de `A` et `B`. C'est le type de retour de [`eigen`](@ref), la fonction de factorisation matricielle correspondante, lorsqu'elle est appelée avec deux arguments matriciels.

Si `F::GeneralizedEigen` est l'objet de factorisation, les valeurs propres peuvent être obtenues via `F.values` et les vecteurs propres comme les colonnes de la matrice `F.vectors`. (Le `k`-ième vecteur propre peut être obtenu à partir de la tranche `F.vectors[:, k]`.)

L'itération de la décomposition produit les composants `F.values` et `F.vectors`.

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

julia> F = eigen(A, B)
GeneralizedEigen{ComplexF64, ComplexF64, Matrix{ComplexF64}, Vector{ComplexF64}}
values:
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im
vectors:
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

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
