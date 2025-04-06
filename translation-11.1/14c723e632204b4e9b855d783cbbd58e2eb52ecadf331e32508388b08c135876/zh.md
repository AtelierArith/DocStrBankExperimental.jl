```
tuple(xs...)
```

构造给定对象的元组。

另见 [`Tuple`](@ref), [`ntuple`](@ref), [`NamedTuple`](@ref)。

# 示例

```jldoctest
julia> tuple(1, 'b', pi)
(1, 'b', π)

julia> ans === (1, 'b', π)
true

julia> Tuple(Real[1, 2, pi])  # 接受一个集合
(1, 2, π)
```
