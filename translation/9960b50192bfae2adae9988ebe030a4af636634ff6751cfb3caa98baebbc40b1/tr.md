```
ones([T=Float64,] dims::Tuple)
ones([T=Float64,] dims...)
```

Bir `Array` oluşturur, eleman tipi `T` olan, `dims` ile belirtilen boyutta tüm elemanları bir olan. Ayrıca [`fill`](@ref), [`zeros`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> ones(1,2)
1×2 Matrix{Float64}:
 1.0  1.0

julia> ones(ComplexF64, 2, 3)
2×3 Matrix{ComplexF64}:
 1.0+0.0im  1.0+0.0im  1.0+0.0im
 1.0+0.0im  1.0+0.0im  1.0+0.0im
```
