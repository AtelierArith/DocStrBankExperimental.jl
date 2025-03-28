```
lq(A) -> S::LQ
```

Berechnen Sie die LQ-Zerlegung von `A`. Die untere dreieckige Komponente der Zerlegung kann aus dem [`LQ`](@ref) Objekt `S` über `S.L` abgerufen werden, und die orthogonale/einheitliche Komponente über `S.Q`, sodass `A ≈ S.L*S.Q`.

Durch Iteration der Zerlegung werden die Komponenten `S.L` und `S.Q` erzeugt.

Die LQ-Zerlegung ist die QR-Zerlegung von `transpose(A)`, und sie ist nützlich, um die Lösung mit minimaler Norm `lq(A) \ b` für ein unterbestimmtes Gleichungssystem zu berechnen (`A` hat mehr Spalten als Zeilen, hat aber vollen Zeilenrang).

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
