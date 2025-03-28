```
DataType <: Type{T}
```

`DataType` representa tipos declarados explícitamente que tienen nombres, supertipos declarados explícitamente y, opcionalmente, parámetros. Cada valor concreto en el sistema es una instancia de algún `DataType`.

# Ejemplos

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
