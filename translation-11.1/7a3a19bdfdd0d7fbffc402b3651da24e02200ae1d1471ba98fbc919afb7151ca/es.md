```
lyap(A, C)
```

Calcula la solución `X` de la ecuación de Lyapunov continua `AX + XA' + C = 0`, donde ningún valor propio de `A` tiene una parte real cero y ningún par de valores propios son conjugados complejos negativos entre sí.

# Ejemplos

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
