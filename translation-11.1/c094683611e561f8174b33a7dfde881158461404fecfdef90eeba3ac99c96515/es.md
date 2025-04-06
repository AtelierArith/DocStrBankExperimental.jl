```
lq(A) -> S::LQ
```

Calcula la descomposición LQ de `A`. El componente triangular inferior de la descomposición se puede obtener del objeto [`LQ`](@ref) `S` a través de `S.L`, y el componente ortogonal/unitario a través de `S.Q`, de modo que `A ≈ S.L*S.Q`.

Iterar la descomposición produce los componentes `S.L` y `S.Q`.

La descomposición LQ es la descomposición QR de `transpose(A)`, y es útil para calcular la solución de mínima norma `lq(A) \ b` para un sistema de ecuaciones subdeterminado (`A` tiene más columnas que filas, pero tiene rango completo de filas).

# Ejemplos

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
Factor L:
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Factor Q: 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # desestructuración a través de la iteración

julia> l == S.L &&  q == S.Q
true
```
