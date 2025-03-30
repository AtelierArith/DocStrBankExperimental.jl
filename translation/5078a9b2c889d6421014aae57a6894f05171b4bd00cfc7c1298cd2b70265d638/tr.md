```
GenelleştirilmişSVD <: Faktörizasyon
```

İki matris `A` ve `B` için genelleştirilmiş tekil değer ayrıştırmasının (SVD) matris faktörizasyon türü, `A = F.U*F.D1*F.R0*F.Q'` ve `B = F.V*F.D2*F.R0*F.Q'` şeklindedir. Bu, [`svd(_, _)`](@ref) fonksiyonunun döndürdüğü türdür, ilgili matris faktörizasyon fonksiyonu.

Bir M-by-N matris `A` ve P-by-N matris `B` için,

  * `U` M-by-M ortogonal bir matristir,
  * `V` P-by-P ortogonal bir matristir,
  * `Q` N-by-N ortogonal bir matristir,
  * `D1` ilk K girişinde 1'ler bulunan M-by-(K+L) diyagonal bir matristir,
  * `D2` üst sağ L-by-L bloğu diyagonal olan P-by-(K+L) bir matristir,
  * `R0` sağdaki (K+L)-by-(K+L) bloğu tekil üst blok üçgen olan (K+L)-by-N bir matristir,

`K+L`, matrisin etkili sayısal derecesidir `[A; B]`.

Ayrıştırmayı yinelemek, `U`, `V`, `Q`, `D1`, `D2` ve `R0` bileşenlerini üretir.

`F.D1` ve `F.D2` girişleri, [genelleştirilmiş SVD](https://www.netlib.org/lapack/lug/node36.html) için LAPACK belgelerinde ve altında çağrılan [xGGSVD3](https://www.netlib.org/lapack/explore-html/d6/db3/dggsvd3_8f.html) rutininde açıklandığı gibi ilişkilidir (LAPACK 3.6.0 ve daha yenilerinde).

# Örnekler

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> F = svd(A, B)
GenelleştirilmişSVD{Float64, Matrix{Float64}, Float64, Vector{Float64}}
U faktörü:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
V faktörü:
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0   0.0
Q faktörü:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
D1 faktörü:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
D2 faktörü:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
R0 faktörü:
2×2 Matrix{Float64}:
 1.41421   0.0
 0.0      -1.41421

julia> F.U*F.D1*F.R0*F.Q'
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> F.V*F.D2*F.R0*F.Q'
2×2 Matrix{Float64}:
 -0.0  1.0
  1.0  0.0
```
