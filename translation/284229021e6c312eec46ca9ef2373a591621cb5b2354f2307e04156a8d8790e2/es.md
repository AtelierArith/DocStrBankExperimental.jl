```
BitArray(undef, dims::Integer...)
BitArray{N}(undef, dims::NTuple{N,Int})
```

Construye un [`BitArray`](@ref) indefinido con las dimensiones dadas. Se comporta de manera idéntica al constructor de [`Array`](@ref). Ver [`undef`](@ref).

# Ejemplos

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
