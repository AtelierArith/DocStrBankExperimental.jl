```
lyap(A, C)
```

Berechnet die Lösung `X` der kontinuierlichen Lyapunov-Gleichung `AX + XA' + C = 0`, wobei kein Eigenwert von `A` einen reellen Teil von null hat und keine zwei Eigenwerte negative komplexe Konjugierte voneinander sind.

# Beispiele

```jldoctest
julia> A = [3. 4.; 5. 6]
2×2 Matrix{Float64}:
 3.0  4.0
 5.0  6.0

julia> B = [1. 1.; 1. 2.]
2×2 Matrix{Float64}:
 1.0  1.0
 1.0  2.0

julia> X = lyap(A, B)
2×2 Matrix{Float64}:
  0.5  -0.5
 -0.5   0.25

julia> A*X + X*A' ≈ -B
true
```
