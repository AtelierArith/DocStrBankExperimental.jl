```
DataType <: Type{T}
```

`DataType` 表示显式声明的具有名称的类型、显式声明的超类型，以及可选的参数。系统中的每个具体值都是某个 `DataType` 的实例。

# 示例

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType

julia> struct Point
           x::Int
           y
       end

julia> typeof(Point)
DataType
```
