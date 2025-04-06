```
valtype(type)
```

获取字典类型的值类型。行为类似于 [`eltype`](@ref)。

# 示例

```jldoctest
julia> valtype(Dict(Int32(1) => "foo"))
String
```
