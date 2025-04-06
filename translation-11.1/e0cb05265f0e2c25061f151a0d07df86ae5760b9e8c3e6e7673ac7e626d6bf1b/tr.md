```
cos(A::AbstractMatrix)
```

Kare matris `A`'nın matris kosinüsünü hesaplar.

Eğer `A` simetrik veya Hermit ise, kosinüsü hesaplamak için özdekompozisyonu ([`eigen`](@ref)) kullanılır. Aksi takdirde, kosinüs [`exp`](@ref) çağrılarak belirlenir.

# Örnekler

```jldoctest
julia> cos(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
  0.291927  -0.708073
 -0.708073   0.291927
```
