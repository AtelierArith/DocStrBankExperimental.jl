```
lq(A) -> S::LQ
```

`A`'nın LQ ayrıştırmasını hesaplayın. Ayrıştırmanın alt üçgen bileşeni, `S` nesnesinden `S.L` aracılığıyla elde edilebilir ve ortogonal/unitary bileşen `S.Q` aracılığıyla elde edilebilir, böylece `A ≈ S.L*S.Q` olur.

Ayrıştırmayı yineleyerek `S.L` ve `S.Q` bileşenlerini elde edersiniz.

LQ ayrıştırması, `transpose(A)`'nın QR ayrıştırmasıdır ve `lq(A) \ b` ifadesi ile bir belirsiz denklemler sistemine ( `A`'nın satır sayısından daha fazla sütunu var, ancak tam satır rütbesine sahip) minimum-norm çözümünü hesaplamak için faydalıdır.

# Örnekler

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
L faktörü:
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q faktörü: 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # yineleme ile parçalama

julia> l == S.L &&  q == S.Q
true
```
