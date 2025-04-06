```
BitArray(undef, dims::Integer...)
BitArray{N}(undef, dims::NTuple{N,Int})
```

Verilen boyutlarla bir `undef` [`BitArray`](@ref) oluşturur. [`Array`](@ref) yapıcısına benzer şekilde davranır. Bakınız [`undef`](@ref).

# Örnekler

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
