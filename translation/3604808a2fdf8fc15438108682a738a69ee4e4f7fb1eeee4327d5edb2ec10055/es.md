```
pushfirst!(colección, elementos...) -> colección
```

Inserta uno o más `elementos` al principio de `colección`.

Esta función se llama `unshift` en muchos otros lenguajes de programación.

# Ejemplos

```jldoctest
julia> pushfirst!([1, 2, 3, 4], 5, 6)
6-element Vector{Int64}:
 5
 6
 1
 2
 3
 4
```
