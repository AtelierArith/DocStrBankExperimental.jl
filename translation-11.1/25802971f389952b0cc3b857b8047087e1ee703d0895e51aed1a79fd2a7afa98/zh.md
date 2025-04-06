```
nonmissingtype(T::Type)
```

如果 `T` 是一个包含 `Missing` 的类型的联合体，则返回一个去除 `Missing` 的新类型。

# 示例

```jldoctest
julia> nonmissingtype(Union{Int64,Missing})
Int64

julia> nonmissingtype(Any)
Any
```

!!! compat "Julia 1.3"
    从 Julia 1.3 开始导出了此函数。

