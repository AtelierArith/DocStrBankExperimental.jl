```
BitArray(undef, dims::Integer...)
BitArray{N}(undef, dims::NTuple{N,Int})
```

주어진 차원으로 `undef` [`BitArray`](@ref)를 생성합니다. [`Array`](@ref) 생성자와 동일하게 동작합니다. [`undef`](@ref)를 참조하세요.

# 예제

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
