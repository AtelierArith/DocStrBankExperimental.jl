```
CholeskyPivoted
```

Tipo de factorización de matriz de la factorización de Cholesky con pivoteo de una matriz densa simétrica/Hermítica positiva semidefinida `A`. Este es el tipo de retorno de [`cholesky(_, ::RowMaximum)`](@ref), la función de factorización de matriz correspondiente.

El factor triangular de Cholesky se puede obtener de la factorización `F::CholeskyPivoted` a través de `F.L` y `F.U`, y la permutación a través de `F.p`, donde `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'` con `Ur = F.U[1:F.rank, :]` y `Lr = F.L[:, 1:F.rank]`, o alternativamente `A ≈ Up' * Up ≈ Lp * Lp'` con `Up = F.U[1:F.rank, invperm(F.p)]` y `Lp = F.L[invperm(F.p), 1:F.rank]`.

Las siguientes funciones están disponibles para objetos `CholeskyPivoted`: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), y [`rank`](@ref).

Iterar la descomposición produce los componentes `L` y `U`.

# Ejemplos

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U factor with rank 1:
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
permutation:
4-element Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # destructuring via iteration

julia> l == C.L && u == C.U
true
```
