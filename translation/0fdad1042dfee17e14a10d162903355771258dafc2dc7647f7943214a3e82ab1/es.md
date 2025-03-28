```
logabsdet(M)
```

Logaritmo del valor absoluto del determinante de la matriz. Equivalente a `(log(abs(det(M))), sign(det(M)))`, pero puede proporcionar mayor precisión y/o velocidad.

# Ejemplos

```jldoctest
julia> A = [-1. 0.; 0. 1.]
2×2 Matrix{Float64}:
 -1.0  0.0
  0.0  1.0

julia> det(A)
-1.0

julia> logabsdet(A)
(0.0, -1.0)

julia> B = [2. 0.; 0. 1.]
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  1.0

julia> det(B)
2.0

julia> logabsdet(B)
(0.6931471805599453, 1.0)
```
