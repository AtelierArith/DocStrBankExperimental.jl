```
BitArray(undef, dims::Integer...)
BitArray{N}(undef, dims::NTuple{N,Int})
```

Konstruiere ein undef [`BitArray`](@ref) mit den gegebenen Dimensionen. Verhält sich identisch zum [`Array`](@ref) Konstruktor. Siehe [`undef`](@ref).

# Beispiele

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
