```
findlast(predicate::Function, A)
```

返回 `A` 中最后一个使 `predicate` 返回 `true` 的元素的索引或键。如果没有这样的元素，则返回 `nothing`。

索引或键与 [`keys(A)`](@ref) 和 [`pairs(A)`](@ref) 返回的类型相同。

# 示例

```jldoctest
julia> A = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> findlast(isodd, A)
3

julia> findlast(x -> x > 5, A) # 返回 nothing，但在 REPL 中不打印

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> findlast(isodd, A)
CartesianIndex(2, 1)
```
