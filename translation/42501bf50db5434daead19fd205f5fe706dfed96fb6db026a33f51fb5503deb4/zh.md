```
isimmutable(v) -> Bool
```

!!! warning
    考虑使用 `!ismutable(v)`，因为 `isimmutable(v)` 将在未来的版本中被 `!ismutable(v)` 替代。 (自 Julia 1.5 起)


返回 `true` 当且仅当值 `v` 是不可变的。有关不可变性的讨论，请参见 [Mutable Composite Types](@ref)。请注意，此函数作用于值，因此如果您给它一个类型，它会告诉您 `DataType` 的值是可变的。

# 示例

```jldoctest
julia> isimmutable(1)
true

julia> isimmutable([1,2])
false
```
