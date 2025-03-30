```
LQ <: Factorizasyon
```

Bir matris `A`'nın `LQ` faktorizasyonunun matris faktorizasyon türü. `LQ` ayrıştırması, `transpose(A)`'nın [`QR`](@ref) ayrıştırmasıdır. Bu, ilgili matris faktorizasyon fonksiyonu olan [`lq`](@ref)'nin dönüş türüdür.

Eğer `S::LQ` faktorizasyon nesnesi ise, alt üçgen bileşeni `S.L` aracılığıyla elde edilebilir ve ortogonal/unitary bileşen `S.Q` aracılığıyla elde edilir, böylece `A ≈ S.L*S.Q` olur.

Ayrıştırmayı yinelemek, bileşenleri `S.L` ve `S.Q` üretir.

# Örnekler

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matris{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matris{Float64}, Vektör{Float64}}
L faktörü:
2×2 Matris{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q faktörü: 2×2 LinearAlgebra.LQPackedQ{Float64, Matris{Float64}, Vektör{Float64}}

julia> S.L * S.Q
2×2 Matris{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # yineleme ile parçalama

julia> l == S.L &&  q == S.Q
true
```
