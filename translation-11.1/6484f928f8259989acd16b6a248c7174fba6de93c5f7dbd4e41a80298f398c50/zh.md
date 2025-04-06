```
sizeof(T::DataType)
sizeof(obj)
```

给定的 `DataType` `T` 的规范二进制表示的大小（以字节为单位），如果有的话。或者对象 `obj` 的大小（以字节为单位），如果它不是 `DataType`。

另请参见 [`Base.summarysize`](@ref)。

# 示例

```jldoctest
julia> sizeof(Float32)
4

julia> sizeof(ComplexF64)
16

julia> sizeof(1.0)
8

julia> sizeof(collect(1.0:10.0))
80

julia> struct StructWithPadding
           x::Int64
           flag::Bool
       end

julia> sizeof(StructWithPadding) # 由于填充，不是字段的 `sizeof` 之和
16

julia> sizeof(Int64) + sizeof(Bool) # 与上面不同
9
```

如果 `DataType` `T` 没有特定的大小，将抛出错误。

```jldoctest
julia> sizeof(AbstractArray)
ERROR: 抽象类型 AbstractArray 没有确定的大小。
Stacktrace:
[...]
```
