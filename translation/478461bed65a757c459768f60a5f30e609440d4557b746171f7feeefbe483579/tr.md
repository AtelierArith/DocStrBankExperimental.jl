```
SVD <: Factorization
```

Bir matrisin tekil değer ayrıştırmasının (SVD) matris faktörizasyon türü `A`. Bu, [`svd(_)`](@ref) ile ilgili matris faktörizasyon fonksiyonunun dönüş türüdür.

Eğer `F::SVD` faktörizasyon nesnesi ise, `U`, `S`, `V` ve `Vt` `F.U`, `F.S`, `F.V` ve `F.Vt` aracılığıyla elde edilebilir; böylece `A = U * Diagonal(S) * Vt`. `S` içindeki tekil değerler azalan sırada sıralanmıştır.

Ayrıştırmayı yinelemek, `U`, `S` ve `V` bileşenlerini üretir.

# Örnekler

```jldoctest
julia> A = [1. 0. 0. 0. 2.; 0. 0. 3. 0. 0.; 0. 0. 0. 0. 0.; 0. 2. 0. 0. 0.]
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> F = svd(A)
SVD{Float64, Float64, Matrix{Float64}, Vector{Float64}}
U faktörü:
4×4 Matrix{Float64}:
 0.0  1.0   0.0  0.0
 1.0  0.0   0.0  0.0
 0.0  0.0   0.0  1.0
 0.0  0.0  -1.0  0.0
tekil değerler:
4-element Vector{Float64}:
 3.0
 2.23606797749979
 2.0
 0.0
Vt faktörü:
4×5 Matrix{Float64}:
 -0.0        0.0  1.0  -0.0  0.0
  0.447214   0.0  0.0   0.0  0.894427
  0.0       -1.0  0.0   0.0  0.0
  0.0        0.0  0.0   1.0  0.0

julia> F.U * Diagonal(F.S) * F.Vt
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> u, s, v = F; # yineleme ile parçalama

julia> u == F.U && s == F.S && v == F.V
true
```
