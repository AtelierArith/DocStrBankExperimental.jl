```
SVD <: Factorización
```

Tipo de factorización de matriz de la descomposición en valores singulares (SVD) de una matriz `A`. Este es el tipo de retorno de [`svd(_)`](@ref), la función de factorización de matriz correspondiente.

Si `F::SVD` es el objeto de factorización, `U`, `S`, `V` y `Vt` se pueden obtener a través de `F.U`, `F.S`, `F.V` y `F.Vt`, de tal manera que `A = U * Diagonal(S) * Vt`. Los valores singulares en `S` están ordenados en orden descendente.

Iterar la descomposición produce los componentes `U`, `S` y `V`.

# Ejemplos

```jldoctest
julia> A = [1. 0. 0. 0. 2.; 0. 0. 3. 0. 0.; 0. 0. 0. 0. 0.; 0. 2. 0. 0. 0.]
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> F = svd(A)
SVD{Float64, Float64, Matrix{Float64}, Vector{Float64}}
U factor:
4×4 Matrix{Float64}:
 0.0  1.0   0.0  0.0
 1.0  0.0   0.0  0.0
 0.0  0.0   0.0  1.0
 0.0  0.0  -1.0  0.0
valores singulares:
4-element Vector{Float64}:
 3.0
 2.23606797749979
 2.0
 0.0
Vt factor:
4×5 Matrix{Float64}:
 -0.0        0.0  1.0  -0.0  0.0
  0.447214   0.0  0.0   0.0  0.894427
  0.0       -1.0  0.0   0.0  0.0
  0.0        0.0  0.0   1.0  0.0

julia> F.U * Diagonal(F.S) * F.Vt
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> u, s, v = F; # desestructuración a través de la iteración

julia> u == F.U && s == F.S && v == F.V
true
```
