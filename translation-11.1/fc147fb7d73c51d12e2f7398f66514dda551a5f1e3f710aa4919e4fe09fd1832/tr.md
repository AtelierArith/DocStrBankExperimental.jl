```
ldiv!(a::Number, B::AbstractArray)
```

Bir dizi `B`'deki her bir girişi bir skalar `a` ile bölerek `B`'yi yerinde günceller. Sağdan skalar bölmek için [`rdiv!`](@ref) kullanın.

# Örnekler

```jldoctest
julia> B = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> ldiv!(2.0, B)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
