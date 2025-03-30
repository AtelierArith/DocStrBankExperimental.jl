```
Vararg{T,N}
```

元组类型 [`Tuple`](@ref) 的最后一个参数可以是特殊值 `Vararg`，表示任意数量的尾随元素。 `Vararg{T,N}` 精确对应 `N` 个类型为 `T` 的元素。最后， `Vararg{T}` 对应零个或多个类型为 `T` 的元素。 `Vararg` 元组类型用于表示 varargs 方法接受的参数（请参见手册中关于 [Varargs Functions](@ref) 的部分。）

另见 [`NTuple`](@ref)。

# 示例

```jldoctest
julia> mytupletype = Tuple{AbstractString, Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```
