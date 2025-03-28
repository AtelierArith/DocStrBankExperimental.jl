```
sylvester(A, B, C)
```

Calcula la solución `X` de la ecuación de Sylvester `AX + XB + C = 0`, donde `A`, `B` y `C` tienen dimensiones compatibles y `A` y `-B` no tienen valores propios con la misma parte real.

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

julia> C = [1. 2.; -2. 1]
2×2 Matrix{Float64}:
  1.0  2.0
 -2.0  1.0

julia> X = sylvester(A, B, C)
2×2 Matrix{Float64}:
 -4.46667   1.93333
  3.73333  -1.8

julia> A*X + X*B ≈ -C
true
```
