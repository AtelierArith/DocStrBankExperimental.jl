```
fieldnames(x::DataType)
```

获取一个元组，包含 `DataType` 的字段名称。

另见 [`propertynames`](@ref), [`hasfield`](@ref)。

# 示例

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
