```
cholesky(A, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

Calcula la factorización de Cholesky pivotada de una matriz densa simétrica positiva semidefinida `A` y devuelve una factorización [`CholeskyPivoted`](@ref). La matriz `A` puede ser una [`Symmetric`](@ref) o [`Hermitian`](@ref) [`AbstractMatrix`](@ref) o una `AbstractMatrix` *perfectamente* simétrica o hermítica.

El factor triangular de Cholesky se puede obtener de la factorización `F` a través de `F.L` y `F.U`, y la permutación a través de `F.p`, donde `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'` con `Ur = F.U[1:F.rank, :]` y `Lr = F.L[:, 1:F.rank]`, o alternativamente `A ≈ Up' * Up ≈ Lp * Lp'` con `Up = F.U[1:F.rank, invperm(F.p)]` y `Lp = F.L[invperm(F.p), 1:F.rank]`.

Las siguientes funciones están disponibles para objetos `CholeskyPivoted`: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), y [`rank`](@ref).

El argumento `tol` determina la tolerancia para determinar el rango. Para valores negativos, la tolerancia es la precisión de la máquina.

Si tienes una matriz `A` que es ligeramente no hermítica debido a errores de redondeo en su construcción, envuélvela en `Hermitian(A)` antes de pasarla a `cholesky` para tratarla como perfectamente hermítica.

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

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
