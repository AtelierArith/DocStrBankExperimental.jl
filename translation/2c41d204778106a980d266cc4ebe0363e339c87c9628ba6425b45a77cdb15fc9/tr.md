```
tan(A::AbstractMatrix)
```

Bir kare matris `A`nın matris tanjantını hesaplar.

Eğer `A` simetrik veya Hermit ise, tanjantı hesaplamak için özdeğişim ([`eigen`](@ref)) kullanılır. Aksi takdirde, tanjant [`exp`](@ref) çağrılarak belirlenir.

# Örnekler

```jldoctest
julia> tan(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 -1.09252  -1.09252
 -1.09252  -1.09252
```
