```
ones([T=Float64,] dims::Tuple)
ones([T=Float64,] dims...)
```

Erstellt ein `Array` mit dem Elementtyp `T`, das aus lauter Einsen besteht und dessen Größe durch `dims` angegeben wird. Siehe auch [`fill`](@ref), [`zeros`](@ref).

# Beispiele

```jldoctest
julia> ones(1,2)
1×2 Matrix{Float64}:
 1.0  1.0

julia> ones(ComplexF64, 2, 3)
2×3 Matrix{ComplexF64}:
 1.0+0.0im  1.0+0.0im  1.0+0.0im
 1.0+0.0im  1.0+0.0im  1.0+0.0im
```
