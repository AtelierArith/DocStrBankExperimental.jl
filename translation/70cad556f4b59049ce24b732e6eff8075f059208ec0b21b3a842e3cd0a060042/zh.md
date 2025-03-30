```
getfield(value, name::Symbol, [order::Symbol])
getfield(value, i::Int, [order::Symbol])
```

通过名称或位置从复合 `value` 中提取字段。可以选择性地为操作定义一个排序。如果字段被声明为 `@atomic`，则强烈建议该规范与该位置的存储兼容。否则，如果未声明为 `@atomic`，则如果指定，则此参数必须为 `:not_atomic`。另请参见 [`getproperty`](@ref Base.getproperty) 和 [`fieldnames`](@ref)。

# 示例

```jldoctest
julia> a = 1//2
1//2

julia> getfield(a, :num)
1

julia> a.num
1

julia> getfield(a, 1)
1
```
