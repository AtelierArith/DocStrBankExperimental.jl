```
Cholesky <: Factorisation
```

Type de factorisation matricielle de la factorisation de Cholesky d'une matrice dense symétrique/Hermite positive définie `A`. C'est le type de retour de [`cholesky`](@ref), la fonction de factorisation matricielle correspondante.

Le facteur triangulaire de Cholesky peut être obtenu à partir de la factorisation `F::Cholesky` via `F.L` et `F.U`, où `A ≈ F.U' * F.U ≈ F.L * F.L'`.

Les fonctions suivantes sont disponibles pour les objets `Cholesky` : [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) et [`isposdef`](@ref).

L'itération de la décomposition produit les composants `L` et `U`.

# Exemples

```jldoctest
julia> A = [4. 12. -16.; 12. 37. -43.; -16. -43. 98.]
3×3 Matrix{Float64}:
   4.0   12.0  -16.0
  12.0   37.0  -43.0
 -16.0  -43.0   98.0

julia> C = cholesky(A)
Cholesky{Float64, Matrix{Float64}}
U factor:
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.U
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.L
3×3 LowerTriangular{Float64, Matrix{Float64}}:
  2.0   ⋅    ⋅
  6.0  1.0   ⋅
 -8.0  5.0  3.0

julia> C.L * C.U == A
true

julia> l, u = C; # destructuration via itération

julia> l == C.L && u == C.U
true
```
