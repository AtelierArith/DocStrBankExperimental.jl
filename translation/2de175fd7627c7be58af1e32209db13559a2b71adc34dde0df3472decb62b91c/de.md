```
DataType <: Type{T}
```

`DataType` repräsentiert explizit deklarierte Typen, die Namen, explizit deklarierte Supertypen und optional Parameter haben. Jeder konkrete Wert im System ist eine Instanz eines `DataType`.

# Beispiele

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
