```
Transpoze
```

Temel lineer cebir nesnesinin, genellikle bir `AbstractVector`/`AbstractMatrix`'in transpoze görünümü için tembel bir sarmalayıcı türü. Genellikle, `Transpose` yapıcısı doğrudan çağrılmamalıdır, bunun yerine [`transpose`](@ref) kullanın. Görünümü somutlaştırmak için [`copy`](@ref) kullanın.

Bu tür, lineer cebir kullanımı için tasarlanmıştır - genel veri manipülasyonu için [`permutedims`](@ref Base.permutedims) kullanın.

# Örnekler

```jldoctest
julia> A = [2 3; 0 0]
2×2 Matrix{Int64}:
 2  3
 0  0

julia> Transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 2  0
 3  0
```
