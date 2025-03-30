```
logabsdet(M)
```

Matris determinantının mutlak değerinin logaritması. `(log(abs(det(M))), sign(det(M)))` ile eşdeğerdir, ancak daha fazla doğruluk ve/veya hız sağlayabilir.

# Örnekler

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
