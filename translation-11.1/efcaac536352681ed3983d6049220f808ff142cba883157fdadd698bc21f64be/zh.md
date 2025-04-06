```
keytype(T::Type{<:AbstractArray})
keytype(A::AbstractArray)
```

返回数组的键类型。这等于 `keys(...)` 结果的 [`eltype`](@ref)，主要是为了与字典接口的兼容性。

# 示例

```jldoctest
julia> keytype([1, 2, 3]) == Int
true

julia> keytype([1 2; 3 4])
CartesianIndex{2}
```

!!! compat "Julia 1.2"
    对于数组，此函数至少需要 Julia 1.2。

