```
dropwhile(pred, iter)
```

Un iterador que descarta elementos de `iter` mientras la predicción `pred` sea verdadera, después devuelve cada elemento.

!!! compat "Julia 1.4"
    Esta función requiere al menos Julia 1.4.


# Ejemplos

```jldoctest
julia> s = collect(1:5)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> collect(Iterators.dropwhile(<(3),s))
3-element Vector{Int64}:
 3
 4
 5
```
