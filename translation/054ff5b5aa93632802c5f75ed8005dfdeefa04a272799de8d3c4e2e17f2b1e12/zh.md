```
cumsum(itr)
```

迭代器的累积和。

另请参见 [`accumulate`](@ref) 以应用其他函数而非 `+`。

!!! compat "Julia 1.5"
    在非数组迭代器上使用 `cumsum` 至少需要 Julia 1.5。


# 示例

```jldoctest
julia> cumsum(1:3)
3-element Vector{Int64}:
 1
 3
 6

julia> cumsum((true, false, true, false, true))
(1, 1, 2, 2, 3)

julia> cumsum(fill(1, 2) for i in 1:3)
3-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]
 [3, 3]
```
