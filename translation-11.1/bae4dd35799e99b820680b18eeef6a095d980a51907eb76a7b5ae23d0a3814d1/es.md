```
UnionAll
```

Una unión de tipos sobre todos los valores de un parámetro de tipo. `UnionAll` se utiliza para describir tipos paramétricos donde los valores de algunos parámetros no son conocidos. Consulte la sección del manual sobre [UnionAll Types](@ref).

# Ejemplos

```jldoctest
julia> typeof(Vector)
UnionAll

julia> typeof(Vector{Int})
DataType
```
