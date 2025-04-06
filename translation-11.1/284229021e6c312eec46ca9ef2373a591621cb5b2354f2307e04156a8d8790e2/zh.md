```
BitArray(undef, dims::Integer...)
BitArray{N}(undef, dims::NTuple{N,Int})
```

构造一个未定义的 [`BitArray`](@ref)，具有给定的维度。行为与 [`Array`](@ref) 构造函数完全相同。参见 [`undef`](@ref)。

# 示例

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
