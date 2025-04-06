```
sin(A::AbstractMatrix)
```

Kare matris `A`'nın matris sinüsünü hesaplar.

Eğer `A` simetrik veya Hermit ise, sinüs hesaplamak için özdekompozisyonu ([`eigen`](@ref)) kullanılır. Aksi takdirde, sinüs [`exp`](@ref) çağrılarak belirlenir.

# Örnekler

```jldoctest
julia> sin(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 0.454649  0.454649
 0.454649  0.454649
```
