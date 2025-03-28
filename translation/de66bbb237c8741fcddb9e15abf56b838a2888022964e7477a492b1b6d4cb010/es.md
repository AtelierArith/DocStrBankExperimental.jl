```
bunchkaufman(A, rook::Bool=false; check = true) -> S::BunchKaufman
```

Calcula la factorización de Bunch-Kaufman [^Bunch1977] de una matriz simétrica o hermítica `A` como `P'*U*D*U'*P` o `P'*L*D*L'*P`, dependiendo de qué triángulo se almacene en `A`, y devuelve un objeto [`BunchKaufman`](@ref). Ten en cuenta que si `A` es simétrica compleja, entonces `U'` y `L'` denotan las transpuestas no conjugadas, es decir, `transpose(U)` y `transpose(L)`.

Iterar la descomposición produce los componentes `S.D`, `S.U` o `S.L` según corresponda dado `S.uplo`, y `S.p`.

Si `rook` es `true`, se utiliza pivoteo de rook. Si `rook` es falso, no se utiliza pivoteo de rook.

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

Las siguientes funciones están disponibles para objetos `BunchKaufman`: [`size`](@ref), `\`, [`inv`](@ref), [`issymmetric`](@ref), [`ishermitian`](@ref), [`getindex`](@ref).

[^Bunch1977]: J R Bunch y L Kaufman, Algunos métodos estables para calcular inercia y resolver sistemas lineales simétricos, Mathematics of Computation 31:137 (1977), 163-179. [url](https://www.ams.org/journals/mcom/1977-31-137/S0025-5718-1977-0428694-0/).

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

julia> S.U*S.D*S.U' - S.P*A*S.P'
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0

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

julia> S.L*S.D*S.L' - A[S.p, S.p]
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
