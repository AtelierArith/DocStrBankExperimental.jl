```
fieldname(x::DataType, i::Integer)
```

获取 `DataType` 的字段 `i` 的名称。

# 示例

```jldoctest
julia> fieldname(Rational, 1)
:num

julia> fieldname(Rational, 2)
:den
```
