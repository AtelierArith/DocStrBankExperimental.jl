```
cholesky(A, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

Calcule la factorisation de Cholesky pivotée d'une matrice dense symétrique semi-définit positive `A` et renvoie une factorisation [`CholeskyPivoted`](@ref). La matrice `A` peut être soit une [`Symmetric`](@ref) soit une [`Hermitian`](@ref) [`AbstractMatrix`](@ref) ou une `AbstractMatrix` *parfaitement* symétrique ou hermitienne.

Le facteur triangulaire de Cholesky peut être obtenu à partir de la factorisation `F` via `F.L` et `F.U`, et la permutation via `F.p`, où `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'` avec `Ur = F.U[1:F.rank, :]` et `Lr = F.L[:, 1:F.rank]`, ou alternativement `A ≈ Up' * Up ≈ Lp * Lp'` avec `Up = F.U[1:F.rank, invperm(F.p)]` et `Lp = F.L[invperm(F.p), 1:F.rank]`.

Les fonctions suivantes sont disponibles pour les objets `CholeskyPivoted` : [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), et [`rank`](@ref).

L'argument `tol` détermine la tolérance pour déterminer le rang. Pour les valeurs négatives, la tolérance est la précision machine.

Si vous avez une matrice `A` qui est légèrement non hermitienne en raison d'erreurs d'arrondi dans sa construction, enveloppez-la dans `Hermitian(A)` avant de la passer à `cholesky` afin de la traiter comme parfaitement hermitienne.

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

# Exemples

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U facteur avec rang 1 :
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
permutation :
4-element Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # déstructuration via itération

julia> l == C.L && u == C.U
true
```
