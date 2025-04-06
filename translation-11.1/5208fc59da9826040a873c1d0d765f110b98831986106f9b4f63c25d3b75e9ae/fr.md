```
cholesky(A, NoPivot(); check = true) -> Cholesky
```

Calculez la factorisation de Cholesky d'une matrice dense symétrique définie positive `A` et renvoyez une [`Cholesky`](@ref) factorisation. La matrice `A` peut être soit une [`Symmetric`](@ref) ou [`Hermitian`](@ref) [`AbstractMatrix`](@ref) ou une `AbstractMatrix` *parfaitement* symétrique ou hermitienne.

Le facteur triangulaire de Cholesky peut être obtenu à partir de la factorisation `F` via `F.L` et `F.U`, où `A ≈ F.U' * F.U ≈ F.L * F.L'`.

Les fonctions suivantes sont disponibles pour les objets `Cholesky` : [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) et [`isposdef`](@ref).

Si vous avez une matrice `A` qui est légèrement non hermitienne en raison d'erreurs d'arrondi dans sa construction, enveloppez-la dans `Hermitian(A)` avant de la passer à `cholesky` afin de la traiter comme parfaitement hermitienne.

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

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
```
