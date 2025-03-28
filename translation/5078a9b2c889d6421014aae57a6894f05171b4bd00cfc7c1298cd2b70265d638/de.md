```
GeneralizedSVD <: Factorization
```

Matrixfaktorisierungstyp der verallgemeinerten singulären Wertzerlegung (SVD) von zwei Matrizen `A` und `B`, sodass `A = F.U*F.D1*F.R0*F.Q'` und `B = F.V*F.D2*F.R0*F.Q'`. Dies ist der Rückgabetyp von [`svd(_, _)`](@ref), der entsprechenden Matrixfaktorierungsfunktion.

Für eine M-by-N-Matrix `A` und eine P-by-N-Matrix `B` gilt:

  * `U` ist eine M-by-M orthogonale Matrix,
  * `V` ist eine P-by-P orthogonale Matrix,
  * `Q` ist eine N-by-N orthogonale Matrix,
  * `D1` ist eine M-by-(K+L) diagonale Matrix mit 1en in den ersten K Einträgen,
  * `D2` ist eine P-by-(K+L) Matrix, deren oberes rechtes L-by-L Block diagonal ist,
  * `R0` ist eine (K+L)-by-N Matrix, deren rechtester (K+L)-by-(K+L) Block nicht singulär oberblocktriangular ist,

`K+L` ist der effektive numerische Rang der Matrix `[A; B]`.

Die Iteration der Zerlegung erzeugt die Komponenten `U`, `V`, `Q`, `D1`, `D2` und `R0`.

Die Einträge von `F.D1` und `F.D2` sind miteinander verbunden, wie in der LAPACK-Dokumentation für die [verallgemeinerte SVD](https://www.netlib.org/lapack/lug/node36.html) und die [xGGSVD3](https://www.netlib.org/lapack/explore-html/d6/db3/dggsvd3_8f.html) Routine, die darunter aufgerufen wird (in LAPACK 3.6.0 und neuer).

# Beispiele

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
