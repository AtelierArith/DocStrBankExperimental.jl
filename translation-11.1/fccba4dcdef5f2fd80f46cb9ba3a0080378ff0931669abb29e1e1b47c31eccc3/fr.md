```
CholeskyPivoted
```

Type de factorisation matricielle de la factorisation de Cholesky pivotée d'une matrice dense symétrique/Hermétique positive semi-définie `A`. C'est le type de retour de [`cholesky(_, ::RowMaximum)`](@ref), la fonction de factorisation matricielle correspondante.

Le facteur triangulaire de Cholesky peut être obtenu à partir de la factorisation `F::CholeskyPivoted` via `F.L` et `F.U`, et la permutation via `F.p`, où `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'` avec `Ur = F.U[1:F.rank, :]` et `Lr = F.L[:, 1:F.rank]`, ou alternativement `A ≈ Up' * Up ≈ Lp * Lp'` avec `Up = F.U[1:F.rank, invperm(F.p)]` et `Lp = F.L[invperm(F.p), 1:F.rank]`.

Les fonctions suivantes sont disponibles pour les objets `CholeskyPivoted` : [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), et [`rank`](@ref).

L'itération de la décomposition produit les composants `L` et `U`.

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
