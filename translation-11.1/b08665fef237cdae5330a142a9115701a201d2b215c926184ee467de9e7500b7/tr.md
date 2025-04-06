```
qr!(A, pivot = NoPivot(); blocksize)
```

`qr!`, [`qr`](@ref) ile aynı işlevi görür, ancak `A`'nın bir alt türü olduğunda [`AbstractMatrix`](@ref), girişi `A` ile üzerine yazarak alan tasarrufu sağlar, kopya oluşturmaktan kaçınır. Faktörizasyon, `A`'nın eleman türü tarafından temsil edilemeyen bir sayı üretirse, örneğin tam sayı türleri için, bir [`InexactError`](@ref) istisnası fırlatılır.

!!! compat "Julia 1.4"
    `blocksize` anahtar kelime argümanı Julia 1.4 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> a = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> qr!(a)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q faktörü: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R faktörü:
2×2 Matrix{Float64}:
 -3.16228  -4.42719
  0.0      -0.632456

julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> qr!(a)
HATA: InexactError: Int64(3.1622776601683795)
Yığın izi:
[...]
```
