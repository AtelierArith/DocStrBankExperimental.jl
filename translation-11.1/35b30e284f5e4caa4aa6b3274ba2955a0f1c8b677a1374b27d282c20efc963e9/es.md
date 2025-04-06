```
prepend!(a::Vector, collections...) -> collection
```

Inserta los elementos de cada `collections` al principio de `a`.

Cuando `collections` especifica múltiples colecciones, se mantiene el orden: los elementos de `collections[1]` aparecerán más a la izquierda en `a`, y así sucesivamente.

!!! compat "Julia 1.6"
    Especificar múltiples colecciones para ser añadidas requiere al menos Julia 1.6.


# Ejemplos

```jldoctest
julia> prepend!([3], [1, 2])
3-element Vector{Int64}:
 1
 2
 3

julia> prepend!([6], [1, 2], [3, 4, 5])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
