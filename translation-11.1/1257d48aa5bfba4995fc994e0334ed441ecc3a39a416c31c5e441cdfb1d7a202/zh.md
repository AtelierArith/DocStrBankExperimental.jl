```
unique!(f, A::AbstractVector)
```

从 `A` 中选择一个值，对于 `f` 应用于 `A` 元素所产生的每个唯一值，然后返回修改后的 A。

!!! compat "Julia 1.1"
    此方法自 Julia 1.1 起可用。


# 示例

```jldoctest
julia> unique!(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4

julia> unique!(n -> n%3, [5, 1, 8, 9, 3, 4, 10, 7, 2, 6])
3-element Vector{Int64}:
 5
 1
 9

julia> unique!(iseven, [2, 3, 5, 7, 9])
2-element Vector{Int64}:
 2
 3
```
