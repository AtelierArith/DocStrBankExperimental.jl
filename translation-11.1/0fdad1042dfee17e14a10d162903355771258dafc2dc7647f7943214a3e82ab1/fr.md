```
logabsdet(M)
```

Logarithme de la valeur absolue du déterminant de la matrice. Équivalent à `(log(abs(det(M))), sign(det(M)))`, mais peut offrir une précision et/ou une vitesse accrues.

# Exemples

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
