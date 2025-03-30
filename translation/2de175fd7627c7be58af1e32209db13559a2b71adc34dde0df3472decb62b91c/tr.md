```
DataType <: Type{T}
```

`DataType`, adlandırılmış türleri, açıkça belirtilmiş üst türleri ve isteğe bağlı olarak parametreleri temsil eder. Sistemdeki her somut değer, bir `DataType` örneğidir.

# Örnekler

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
