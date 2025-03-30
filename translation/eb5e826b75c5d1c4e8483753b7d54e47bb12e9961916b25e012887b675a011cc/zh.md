```
issubset(a, b) -> Bool
⊆(a, b) -> Bool
⊇(b, a) -> Bool
```

确定 `a` 的每个元素是否也在 `b` 中，使用 [`in`](@ref)。

另见 [`⊊`](@ref)，[`⊈`](@ref)，[`∩`](@ref intersect)，[`∪`](@ref union)，[`contains`](@ref)。

# 示例

```jldoctest
julia> issubset([1, 2], [1, 2, 3])
true

julia> [1, 2, 3] ⊆ [1, 2]
false

julia> [1, 2, 3] ⊇ [1, 2]
true
```
