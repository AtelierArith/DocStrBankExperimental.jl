```
GeneralizedSVD <: Factorization
```

Tipo de factorización de matriz de la descomposición en valores singulares generalizada (SVD) de dos matrices `A` y `B`, tal que `A = F.U*F.D1*F.R0*F.Q'` y `B = F.V*F.D2*F.R0*F.Q'`. Este es el tipo de retorno de [`svd(_, _)`](@ref), la función de factorización de matriz correspondiente.

Para una matriz `A` de M por N y una matriz `B` de P por N,

  * `U` es una matriz ortogonal de M por M,
  * `V` es una matriz ortogonal de P por P,
  * `Q` es una matriz ortogonal de N por N,
  * `D1` es una matriz diagonal de M por (K+L) con 1s en las primeras K entradas,
  * `D2` es una matriz de P por (K+L) cuyo bloque superior derecho de L por L es diagonal,
  * `R0` es una matriz de (K+L) por N cuyo bloque superior derecho de (K+L) por (K+L) es no singular y triangular superior,

`K+L` es el rango numérico efectivo de la matriz `[A; B]`.

Iterar la descomposición produce los componentes `U`, `V`, `Q`, `D1`, `D2` y `R0`.

Las entradas de `F.D1` y `F.D2` están relacionadas, como se explica en la documentación de LAPACK para el [SVD generalizado](https://www.netlib.org/lapack/lug/node36.html) y la rutina [xGGSVD3](https://www.netlib.org/lapack/explore-html/d6/db3/dggsvd3_8f.html) que se llama por debajo (en LAPACK 3.6.0 y versiones más nuevas).

# Ejemplos

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> F = svd(A, B)
GeneralizedSVD{Float64, Matrix{Float64}, Float64, Vector{Float64}}
U factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
V factor:
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0   0.0
Q factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
D1 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
D2 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
R0 factor:
2×2 Matrix{Float64}:
 1.41421   0.0
 0.0      -1.41421

julia> F.U*F.D1*F.R0*F.Q'
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> F.V*F.D2*F.R0*F.Q'
2×2 Matrix{Float64}:
 -0.0  1.0
  1.0  0.0
```
