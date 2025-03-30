```
diagind(M::AbstractMatrix, k::Integer = 0, indstyle::IndexStyle = IndexLinear())
diagind(M::AbstractMatrix, indstyle::IndexStyle = IndexLinear())
```

一个 `AbstractRange`，给出矩阵 `M` 的第 `k` 条对角线的索引。可以选择性地指定索引样式，以确定返回的范围类型。如果 `indstyle isa IndexLinear`（默认），则返回 `AbstractRange{Integer}`。另一方面，如果 `indstyle isa IndexCartesian`，则返回 `AbstractRange{CartesianIndex{2}}`。

如果未提供 `k`，则假定为 `0`（对应主对角线）。

另请参见: [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref)。

# 示例

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A, -1)
2:4:6

julia> diagind(A, IndexCartesian())
StepRangeLen(CartesianIndex(1, 1), CartesianIndex(1, 1), 3)
```

!!! compat "Julia 1.11"
    指定 `IndexStyle` 至少需要 Julia 1.11。

