```
splice!(a::Vector, index::Integer, [replacement]) -> item
```

移除给定索引处的项，并返回被移除的项。后续项向左移动以填补产生的空缺。如果指定了替换值，则将有序集合中的替换值插入到被移除的项的位置。

另见: [`replace`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`pop!`](@ref), [`popat!`](@ref)。

# 示例

```jldoctest
julia> A = [6, 5, 4, 3, 2, 1]; splice!(A, 5)
2

julia> A
5-element Vector{Int64}:
 6
 5
 4
 3
 1

julia> splice!(A, 5, -1)
1

julia> A
5-element Vector{Int64}:
  6
  5
  4
  3
 -1

julia> splice!(A, 1, [-1, -2, -3])
6

julia> A
7-element Vector{Int64}:
 -1
 -2
 -3
  5
  4
  3
 -1
```

要在不移除任何项的情况下在索引 `n` 之前插入 `replacement`，请使用 `splice!(collection, n:n-1, replacement)`。
