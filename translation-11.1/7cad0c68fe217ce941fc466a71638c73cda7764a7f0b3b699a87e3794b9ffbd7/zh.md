```
keytype(type)
```

获取字典类型的键类型。行为类似于 [`eltype`](@ref)。

# 示例

```jldoctest
julia> keytype(Dict(Int32(1) => "foo"))
Int32
```
