```
findfirst(A)
```

返回 `A` 中第一个 `true` 值的索引或键。如果未找到此类值，则返回 `nothing`。要搜索其他类型的值，请将谓词作为第一个参数传递。

索引或键与 [`keys(A)`](@ref) 和 [`pairs(A)`](@ref) 返回的类型相同。

另请参见：[`findall`](@ref), [`findnext`](@ref), [`findlast`](@ref), [`searchsortedfirst`](@ref)。

# 示例

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findfirst(A)
3

julia> findfirst(falses(3)) # 返回 nothing，但在 REPL 中未打印

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findfirst(A)
CartesianIndex(2, 1)
```
