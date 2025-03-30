```
Adjoint
```

Temel lineer cebir nesnesinin, genellikle bir `AbstractVector`/`AbstractMatrix` olan, adjoint görünümünün tembel sarmalayıcı türü. Genellikle, `Adjoint` yapıcısı doğrudan çağrılmamalıdır, bunun yerine [`adjoint`](@ref) kullanın. Görünümü somutlaştırmak için [`copy`](@ref) kullanın.

Bu tür, lineer cebir kullanımı için tasarlanmıştır - genel veri manipülasyonu için [`permutedims`](@ref Base.permutedims) kullanın.

# Örnekler

```jldoctest
julia> A = [3+2im 9+2im; 0 0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> Adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im
```
