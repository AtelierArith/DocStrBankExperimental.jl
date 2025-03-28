```
cholesky(A, NoPivot(); check = true) -> Cholesky
```

Calcula la factorización de Cholesky de una matriz densa simétrica definida positiva `A` y devuelve una [`Cholesky`](@ref) factorización. La matriz `A` puede ser una [`Symmetric`](@ref) o [`Hermitian`](@ref) [`AbstractMatrix`](@ref) o una `AbstractMatrix` *perfectamente* simétrica o hermítica.

El factor triangular de Cholesky se puede obtener de la factorización `F` a través de `F.L` y `F.U`, donde `A ≈ F.U' * F.U ≈ F.L * F.L'`.

Las siguientes funciones están disponibles para los objetos `Cholesky`: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) y [`isposdef`](@ref).

Si tienes una matriz `A` que es ligeramente no hermítica debido a errores de redondeo en su construcción, envuélvela en `Hermitian(A)` antes de pasarla a `cholesky` para tratarla como perfectamente hermítica.

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

# Ejemplos

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
