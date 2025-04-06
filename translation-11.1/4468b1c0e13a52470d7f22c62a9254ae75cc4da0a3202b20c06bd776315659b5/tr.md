```
rdiv!(A::AbstractArray, b::Number)
```

Bir dizideki her bir girişi bir skalar `b` ile bölerek `A`'yı yerinde günceller. Soldan skalar bölmek için [`ldiv!`](@ref) kullanın.

# Örnekler

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> rdiv!(A, 2.0)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
