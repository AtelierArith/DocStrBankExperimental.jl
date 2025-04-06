```
lu!(A, pivot = RowMaximum(); check = true, allowsingular = false) -> LU
```

`lu!` aynı [`lu`](@ref) ile aynı işlevi görür, ancak girdi `A`'yı kopyalamak yerine üzerine yazarak yer tasarrufu sağlar. Faktörizasyon, `A`'nın eleman türü tarafından temsil edilemeyen bir sayı üretirse, örneğin tam sayı türleri için, bir [`InexactError`](@ref) istisnası fırlatılır.

!!! compat "Julia 1.11"
    `allowsingular` anahtar argümanı Julia 1.11'de eklendi.


# Örnekler

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Matrix{Float64}:
 4.0  3.0
 6.0  3.0

julia> F = lu!(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L faktörü:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U faktörü:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> lu!(iA)
HATA: InexactError: Int64(0.6666666666666666)
Yığın izi:
[...]
```
