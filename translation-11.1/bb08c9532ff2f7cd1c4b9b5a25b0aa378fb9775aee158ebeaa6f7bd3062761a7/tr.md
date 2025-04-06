```
zeros([T=Float64,] dims::Tuple)
zeros([T=Float64,] dims...)
```

Bir `Array` oluşturur, eleman tipi `T` olan, `dims` ile belirtilen boyutta tüm elemanları sıfır olan. Ayrıca [`fill`](@ref), [`ones`](@ref), [`zero`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> zeros(1)
1-element Vector{Float64}:
 0.0

julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0
```
