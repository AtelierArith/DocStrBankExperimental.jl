```
findlast(A)
```

返回 `A` 中最后一个 `true` 值的索引或键。如果 `A` 中没有 `true` 值，则返回 `nothing`。

索引或键与 [`keys(A)`](@ref) 和 [`pairs(A)`](@ref) 返回的类型相同。

另请参见：[`findfirst`](@ref)，[`findprev`](@ref)，[`findall`](@ref)。

# 示例

```jldoctest
julia> A = [true, false, true, false]
4-element Vector{Bool}:
 1
 0
 1
 0

julia> findlast(A)
3

julia> A = falses(2,2);

julia> findlast(A) # 返回 nothing，但在 REPL 中未打印

julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> findlast(A)
CartesianIndex(2, 1)
```
