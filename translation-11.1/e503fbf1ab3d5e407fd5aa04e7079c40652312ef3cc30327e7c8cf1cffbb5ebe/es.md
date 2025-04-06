```
cross(x, y)
×(x,y)
```

Calcula el producto cruzado de dos vectores de 3 dimensiones.

# Ejemplos

```jldoctest
julia> a = [0;1;0]
3-element Vector{Int64}:
 0
 1
 0

julia> b = [0;0;1]
3-element Vector{Int64}:
 0
 0
 1

julia> cross(a,b)
3-element Vector{Int64}:
 1
 0
 0
```
