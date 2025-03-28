```
BunchKaufman <: Factorization
```

Tipo de factorización de matriz de la factorización de Bunch-Kaufman de una matriz simétrica o hermítica `A` como `P'UDU'P` o `P'LDL'P`, dependiendo de si el triángulo superior (el predeterminado) o el triángulo inferior se almacena en `A`. Si `A` es simétrica compleja, entonces `U'` y `L'` denotan las transpuestas no conjugadas, es decir, `transpose(U)` y `transpose(L)`, respectivamente. Este es el tipo de retorno de [`bunchkaufman`](@ref), la función de factorización de matriz correspondiente.

Si `S::BunchKaufman` es el objeto de factorización, los componentes se pueden obtener a través de `S.D`, `S.U` o `S.L` según corresponda dado `S.uplo`, y `S.p`.

Iterar la descomposición produce los componentes `S.D`, `S.U` o `S.L` según corresponda dado `S.uplo`, y `S.p`.

# Ejemplos

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A se envuelve internamente por Symmetric(A)
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D factor:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 -0.333333  0.0
  0.0       3.0
U factor:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.666667
  ⋅   1.0
permutation:
2-element Vector{Int64}:
 1
 2

julia> d, u, p = S; # desestructuración a través de la iteración

julia> d == S.D && u == S.U && p == S.p
true

julia> S = bunchkaufman(Symmetric(A, :L))
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D factor:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 3.0   0.0
 0.0  -0.333333
L factor:
2×2 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0        ⋅
 0.666667  1.0
permutation:
2-element Vector{Int64}:
 2
 1
```
