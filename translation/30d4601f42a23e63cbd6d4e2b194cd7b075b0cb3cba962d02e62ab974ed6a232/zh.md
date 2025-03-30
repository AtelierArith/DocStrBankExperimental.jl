```
findprev(A, i)
```

查找在 `i` 之前或包括 `i` 的 `A` 中 `true` 元素的前一个索引，如果未找到则返回 `nothing`。

索引与 [`keys(A)`](@ref) 和 [`pairs(A)`](@ref) 返回的类型相同。

另请参见: [`findnext`](@ref), [`findfirst`](@ref), [`findall`](@ref)。

# 示例

```jldoctest
julia> A = [false, false, true, true]
4-element Vector{Bool}:
 0
 0
 1
 1

julia> findprev(A, 3)
3

julia> findprev(A, 1) # 返回 nothing，但在 REPL 中未打印

julia> A = [false false; true true]
2×2 Matrix{Bool}:
 0  0
 1  1

julia> findprev(A, CartesianIndex(2, 1))
CartesianIndex(2, 1)
```
