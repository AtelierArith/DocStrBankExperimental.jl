```
Union{}
```

`Union{}`，空的 [`Union`](@ref) 类型，是没有值的类型。也就是说，对于任何 `x`，它具有定义属性 `isa(x, Union{}) == false`。`Base.Bottom` 被定义为它的别名，`Union{}` 的类型是 `Core.TypeofBottom`。

# 示例

```jldoctest
julia> isa(nothing, Union{})
false
```
