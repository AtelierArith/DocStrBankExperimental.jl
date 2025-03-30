```
findnext(A, i)
```

查找 `A` 中 `i` 之后或包括 `i` 的下一个 `true` 元素的索引，如果未找到则返回 `nothing`。

索引与 [`keys(A)`](@ref) 和 [`pairs(A)`](@ref) 返回的类型相同。

# 示例

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findnext(A, 1)
3

julia> findnext(A, 4) # 返回 nothing，但在 REPL 中不打印

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findnext(A, CartesianIndex(1, 1))
CartesianIndex(2, 1)
```
