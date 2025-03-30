```
LDLt <: Factorizasyon
```

Gerçek [`SymTridiagonal`](@ref) matris `S` için `S = L*Diagonal(d)*L'` şeklinde `LDLt` faktorizasyonunun matris faktorizasyon türü, burada `L` bir [`UnitLowerTriangular`](@ref) matris ve `d` bir vektördür. `F = ldlt(S)` şeklindeki bir `LDLt` faktorizasyonunun ana kullanımı, `Sx = b` doğrusal denklemler sistemini `F\b` ile çözmektir. Bu, ilgili matris faktorizasyon fonksiyonu olan [`ldlt`](@ref) için dönüş türüdür.

Faktorizasyonun bireysel bileşenleri `F::LDLt` aracılığıyla `getproperty` ile erişilebilir:

| Bileşen | Açıklama                                    |
|:-------:|:------------------------------------------- |
|  `F.L`  | `LDLt`'nin `L` (birim alt üçgen) kısmı      |
|  `F.D`  | `LDLt`'nin `D` (diyagonal) kısmı            |
| `F.Lt`  | `LDLt`'nin `Lt` (birim üst üçgen) kısmı     |
|  `F.d`  | `D`'nin diyagonal değerleri `Vector` olarak |

# Örnekler

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> F = ldlt(S)
LDLt{Float64, SymTridiagonal{Float64, Vector{Float64}}}
L faktörü:
3×3 UnitLowerTriangular{Float64, SymTridiagonal{Float64, Vector{Float64}}}:
 1.0        ⋅         ⋅
 0.333333  1.0        ⋅
 0.0       0.545455  1.0
D faktörü:
3×3 Diagonal{Float64, Vector{Float64}}:
 3.0   ⋅        ⋅
  ⋅   3.66667   ⋅
  ⋅    ⋅       3.90909
```
