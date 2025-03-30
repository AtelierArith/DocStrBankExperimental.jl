```
nfields(x) -> Int
```

获取给定对象中的字段数量。

# 示例

```jldoctest
julia> a = 1//2;

julia> nfields(a)
2

julia> b = 1
1

julia> nfields(b)
0

julia> ex = ErrorException("我做了一件坏事");

julia> nfields(ex)
1
```

在这些示例中，`a` 是一个 [`Rational`](@ref)，它有两个字段。`b` 是一个 `Int`，它是一个没有任何字段的原始位类型。`ex` 是一个 [`ErrorException`](@ref)，它有一个字段。
