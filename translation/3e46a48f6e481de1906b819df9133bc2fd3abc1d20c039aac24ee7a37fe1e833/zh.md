```
findall(A)
```

返回一个向量 `I`，其中包含 `A` 的 `true` 索引或键。如果 `A` 中没有这样的元素，则返回一个空数组。要搜索其他类型的值，请将谓词作为第一个参数传递。

索引或键与 [`keys(A)`](@ref) 和 [`pairs(A)`](@ref) 返回的类型相同。

另请参见：[`findfirst`](@ref)，[`searchsorted`](@ref)。

# 示例

```jldoctest
julia> A = [true, false, false, true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> findall(A)
2-element Vector{Int64}:
 1
 4

julia> A = [true false; false true]
2×2 Matrix{Bool}:
 1  0
 0  1

julia> findall(A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 2)

julia> findall(falses(3))
Int64[]
```
