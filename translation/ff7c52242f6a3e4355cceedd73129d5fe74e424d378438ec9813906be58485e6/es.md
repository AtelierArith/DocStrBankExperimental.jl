```
LQ <: Factorización
```

Tipo de factorización de matriz de la factorización `LQ` de una matriz `A`. La descomposición `LQ` es la descomposición [`QR`](@ref) de `transpose(A)`. Este es el tipo de retorno de [`lq`](@ref), la función de factorización de matriz correspondiente.

Si `S::LQ` es el objeto de factorización, el componente triangular inferior se puede obtener a través de `S.L`, y el componente ortogonal/unitario a través de `S.Q`, de modo que `A ≈ S.L*S.Q`.

Iterar la descomposición produce los componentes `S.L` y `S.Q`.

# Ejemplos

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
L factor:
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q factor: 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # desestructuración a través de la iteración

julia> l == S.L &&  q == S.Q
true
```
