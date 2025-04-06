```
Cholesky <: Factorización
```

Tipo de factorización de matriz de la factorización de Cholesky de una matriz densa simétrica/Hermítica definida positiva `A`. Este es el tipo de retorno de [`cholesky`](@ref), la función de factorización de matriz correspondiente.

El factor triangular de Cholesky se puede obtener de la factorización `F::Cholesky` a través de `F.L` y `F.U`, donde `A ≈ F.U' * F.U ≈ F.L * F.L'`.

Las siguientes funciones están disponibles para objetos `Cholesky`: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) y [`isposdef`](@ref).

Iterar la descomposición produce los componentes `L` y `U`.

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

julia> l, u = C; # desestructuración a través de la iteración

julia> l == C.L && u == C.U
true
```
