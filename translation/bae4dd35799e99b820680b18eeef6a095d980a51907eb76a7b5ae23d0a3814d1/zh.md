```
UnionAll
```

一个类型参数的所有值的类型的并集。`UnionAll` 用于描述参数化类型，其中某些参数的值是未知的。请参阅手册中关于 [UnionAll Types](@ref) 的部分。

# 示例

```jldoctest
julia> typeof(Vector)
UnionAll

julia> typeof(Vector{Int})
DataType
```
