```
Schur <: Factorization
```

Type de factorisation matricielle de la factorisation de Schur d'une matrice `A`. C'est le type de retour de [`schur(_)`](@ref), la fonction de factorisation matricielle correspondante.

Si `F::Schur` est l'objet de factorisation, le facteur de Schur (quasi) triangulaire peut être obtenu via `F.Schur` ou `F.T` et les vecteurs de Schur orthogonaux/unitaires via `F.vectors` ou `F.Z` de sorte que `A = F.vectors * F.Schur * F.vectors'`. Les valeurs propres de `A` peuvent être obtenues avec `F.values`.

L'itération de la décomposition produit les composants `F.T`, `F.Z` et `F.values`.

# Exemples

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T factor:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z factor:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
eigenvalues:
2-element Vector{Float64}:
  3.0
 -2.0

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # destructuring via iteration

julia> t == F.T && z == F.Z && vals == F.values
true
```
