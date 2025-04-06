```
subtypes(T::DataType)
```

返回数据类型 `T` 的直接子类型列表。请注意，所有当前加载的子类型都包括在内，包括那些在当前模块中不可见的子类型。

另请参见 [`supertype`](@ref), [`supertypes`](@ref), [`methodswith`](@ref)。

# 示例

```jldoctest
julia> subtypes(Integer)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```
