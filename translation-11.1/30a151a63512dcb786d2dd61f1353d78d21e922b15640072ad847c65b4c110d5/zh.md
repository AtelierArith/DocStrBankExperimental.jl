```
Iterators.flatmap(f, iterators...)
```

等价于 `flatten(map(f, iterators...))`。

另见 [`Iterators.flatten`](@ref), [`Iterators.map`](@ref)。

!!! compat "Julia 1.9"
    此函数在 Julia 1.9 中添加。


# 示例

```jldoctest
julia> Iterators.flatmap(n -> -n:2:n, 1:3) |> collect
9-element Vector{Int64}:
 -1
  1
 -2
  0
  2
 -3
 -1
  1
  3

julia> stack(n -> -n:2:n, 1:3)
ERROR: DimensionMismatch: stack expects uniform slices, got axes(x) == (1:3,) while first had (1:2,)
[...]

julia> Iterators.flatmap(n -> (-n, 10n), 1:2) |> collect
4-element Vector{Int64}:
 -1
 10
 -2
 20

julia> ans == vec(stack(n -> (-n, 10n), 1:2))
true
```
