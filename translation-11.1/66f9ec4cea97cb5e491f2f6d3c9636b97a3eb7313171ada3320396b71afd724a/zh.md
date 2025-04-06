```
valtype(T::Type{<:AbstractArray})
valtype(A::AbstractArray)
```

返回数组的值类型。这与 [`eltype`](@ref) 相同，主要是为了与字典接口的兼容性。

# 示例

```jldoctest
julia> valtype(["one", "two", "three"])
String
```

!!! compat "Julia 1.2"
    对于数组，此函数至少需要 Julia 1.2。

