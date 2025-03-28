```
deleteat!(a::Vector, inds)
```

Elimina los elementos en los índices dados por `inds`, y devuelve el `a` modificado. Los elementos subsiguientes se desplazan para llenar el hueco resultante.

`inds` puede ser un iterador o una colección de índices enteros únicos y ordenados, o un vector booleano de la misma longitud que `a` con `true` indicando las entradas a eliminar.

# Ejemplos

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], [true, false, true, false, true, false])
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], (2, 2))
ERROR: ArgumentError: indices must be unique and sorted
Stacktrace:
[...]
```
