```
Eigen <: Factorization
```

Type de factorisation de matrice de la décomposition en valeurs propres/spectrales d'une matrice carrée `A`. C'est le type de retour de [`eigen`](@ref), la fonction de factorisation de matrice correspondante.

Si `F::Eigen` est l'objet de factorisation, les valeurs propres peuvent être obtenues via `F.values` et les vecteurs propres comme les colonnes de la matrice `F.vectors`. (Le `k`-ième vecteur propre peut être obtenu à partir de la tranche `F.vectors[:, k]`.)

L'itération de la décomposition produit les composants `F.values` et `F.vectors`.

# Exemples

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
