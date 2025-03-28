```
SVD <: Factorization
```

Type de factorisation matricielle de la décomposition en valeurs singulières (SVD) d'une matrice `A`. C'est le type de retour de [`svd(_)`](@ref), la fonction de factorisation matricielle correspondante.

Si `F::SVD` est l'objet de factorisation, `U`, `S`, `V` et `Vt` peuvent être obtenus via `F.U`, `F.S`, `F.V` et `F.Vt`, de sorte que `A = U * Diagonal(S) * Vt`. Les valeurs singulières dans `S` sont triées par ordre décroissant.

L'itération de la décomposition produit les composants `U`, `S` et `V`.

# Exemples

```jldoctest
julia> A = [1. 0. 0. 0. 2.; 0. 0. 3. 0. 0.; 0. 0. 0. 0. 0.; 0. 2. 0. 0. 0.]
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> F = svd(A)
SVD{Float64, Float64, Matrix{Float64}, Vector{Float64}}
U factor:
4×4 Matrix{Float64}:
 0.0  1.0   0.0  0.0
 1.0  0.0   0.0  0.0
 0.0  0.0   0.0  1.0
 0.0  0.0  -1.0  0.0
valeurs singulières:
4-element Vector{Float64}:
 3.0
 2.23606797749979
 2.0
 0.0
Vt factor:
4×5 Matrix{Float64}:
 -0.0        0.0  1.0  -0.0  0.0
  0.447214   0.0  0.0   0.0  0.894427
  0.0       -1.0  0.0   0.0  0.0
  0.0        0.0  0.0   1.0  0.0

julia> F.U * Diagonal(F.S) * F.Vt
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> u, s, v = F; # déstructuration via itération

julia> u == F.U && s == F.S && v == F.V
true
```
