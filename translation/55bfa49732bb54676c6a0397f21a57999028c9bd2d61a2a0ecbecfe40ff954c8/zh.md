```
splice!(a::Vector, indices, [replacement]) -> items
```

在指定的索引处移除项目，并返回一个包含被移除项目的集合。后续项目向左移动以填补结果中的空缺。如果指定了替换值，则将有序集合中的替换值插入到被移除项目的位置；在这种情况下，`indices` 必须是 `AbstractUnitRange`。

要在不移除任何项目的情况下在索引 `n` 之前插入 `replacement`，请使用 `splice!(collection, n:n-1, replacement)`。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


!!! compat "Julia 1.5"
    在 Julia 1.5 之前，`indices` 必须始终是 `UnitRange`。


!!! compat "Julia 1.8"
    在 Julia 1.8 之前，如果在替换值中进行拼接，`indices` 必须是 `UnitRange`。


# 示例

```jldoctest
julia> A = [-1, -2, -3, 5, 4, 3, -1]; splice!(A, 4:3, 2)
Int64[]

julia> A
8-element Vector{Int64}:
 -1
 -2
 -3
  2
  5
  4
  3
 -1
```
