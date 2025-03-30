```
LU <: Factorizasyon
```

Kare matris `A`'nın `LU` faktorizasyonunun matris faktorizasyon türü. Bu, ilgili matris faktorizasyon fonksiyonu olan [`lu`](@ref) için dönüş türüdür.

Faktorizasyonun bireysel bileşenlerine `F::LU` aracılığıyla [`getproperty`](@ref) ile erişilebilir:

| Bileşen | Açıklama                             |
|:------- |:------------------------------------ |
| `F.L`   | `LU`'nun `L` (birim alt üçgen) kısmı |
| `F.U`   | `LU`'nun `U` (üst üçgen) kısmı       |
| `F.p`   | (sağ) permütasyon `Vector`           |
| `F.P`   | (sağ) permütasyon `Matrix`           |

Faktorizasyonu yinelemek, `F.L`, `F.U` ve `F.p` bileşenlerini üretir.

# Örnekler

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L faktörü:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U faktörü:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # yineleme ile parçalama

julia> l == F.L && u == F.U && p == F.p
true
```
