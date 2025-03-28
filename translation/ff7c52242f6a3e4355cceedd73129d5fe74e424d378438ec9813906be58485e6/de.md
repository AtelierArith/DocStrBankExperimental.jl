```
LQ <: Faktorisierung
```

Matrixfaktorisierungstyp der `LQ`-Faktorisierung einer Matrix `A`. Die `LQ`-Zerlegung ist die [`QR`](@ref) Zerlegung von `transpose(A)`. Dies ist der Rückgabetyp von [`lq`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Wenn `S::LQ` das Faktorisierungsobjekt ist, kann die untere dreieckige Komponente über `S.L` und die orthogonale/einheitliche Komponente über `S.Q` abgerufen werden, sodass `A ≈ S.L*S.Q`.

Das Iterieren über die Zerlegung erzeugt die Komponenten `S.L` und `S.Q`.

# Beispiele

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
L-Faktor:
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q-Faktor: 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # Destrukturierung über Iteration

julia> l == S.L &&  q == S.Q
true
```
