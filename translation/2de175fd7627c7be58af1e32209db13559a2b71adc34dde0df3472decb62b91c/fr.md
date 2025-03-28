```
DataType <: Type{T}
```

`DataType` représente des types déclarés explicitement qui ont des noms, des supertypes déclarés explicitement et, éventuellement, des paramètres. Chaque valeur concrète dans le système est une instance de quelque `DataType`.

# Exemples

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
