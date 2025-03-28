```
partialsortperm(v, k; by=identity, lt=isless, rev=false)
```

Devuelve una permutación parcial `I` del vector `v`, de modo que `v[I]` devuelve los valores de una versión completamente ordenada de `v` en el índice `k`. Si `k` es un rango, se devuelve un vector de índices; si `k` es un entero, se devuelve un único índice. El orden se especifica utilizando las mismas palabras clave que `sort!`. La permutación es estable: los índices de elementos iguales aparecerán en orden ascendente.

Esta función es equivalente a, pero más eficiente que, llamar a `sortperm(...)[k]`.

# Ejemplos

```jldoctest
julia> v = [3, 1, 2, 1];

julia> v[partialsortperm(v, 1)]
1

julia> p = partialsortperm(v, 1:3)
3-element view(::Vector{Int64}, 1:3) with eltype Int64:
 2
 4
 3

julia> v[p]
3-element Vector{Int64}:
 1
 1
 2
```
