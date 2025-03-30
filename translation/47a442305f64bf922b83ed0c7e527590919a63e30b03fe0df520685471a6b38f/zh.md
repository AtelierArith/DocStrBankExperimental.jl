```
end
```

`end` 标志着一组表达式的结束，例如 [`module`](@ref), [`struct`](@ref), [`mutable struct`](@ref), [`begin`](@ref), [`let`](@ref), [`for`](@ref) 等。

`end` 也可以在索引时使用，表示集合的最后一个索引或数组某个维度的最后一个索引。

# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64, 2}:
 1  2
 3  4

julia> A[end, :]
2-element Array{Int64, 1}:
 3
 4
```
