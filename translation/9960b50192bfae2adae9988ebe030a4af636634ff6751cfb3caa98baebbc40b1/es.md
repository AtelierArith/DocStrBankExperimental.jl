```
ones([T=Float64,] dims::Tuple)
ones([T=Float64,] dims...)
```

Crea un `Array`, con tipo de elemento `T`, de todos unos con tamaño especificado por `dims`. Ver también [`fill`](@ref), [`zeros`](@ref).

# Ejemplos

```jldoctest
julia> ones(1,2)
1×2 Matrix{Float64}:
 1.0  1.0

julia> ones(ComplexF64, 2, 3)
2×3 Matrix{ComplexF64}:
 1.0+0.0im  1.0+0.0im  1.0+0.0im
 1.0+0.0im  1.0+0.0im  1.0+0.0im
```
