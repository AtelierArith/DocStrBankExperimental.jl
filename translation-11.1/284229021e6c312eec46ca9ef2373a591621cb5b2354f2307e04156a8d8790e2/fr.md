```
BitArray(undef, dims::Integer...)
BitArray{N}(undef, dims::NTuple{N,Int})
```

Construit un [`BitArray`](@ref) undef avec les dimensions données. Comporte de manière identique au constructeur [`Array`](@ref). Voir [`undef`](@ref).

# Exemples

```julia-repl
julia> BitArray(undef, 2, 2)
2×2 BitMatrix:
 0  0
 0  0

julia> BitArray(undef, (3, 1))
3×1 BitMatrix:
 0
 0
 0
```
