```
flatten(iter)
```

Dado un iterador que produce iteradores, devuelve un iterador que produce los elementos de esos iteradores. Dicho de otra manera, los elementos del iterador de argumento se concatenan.

# Ejemplos

```jldoctest
julia> collect(Iterators.flatten((1:2, 8:9)))
4-element Vector{Int64}:
 1
 2
 8
 9

julia> [(x,y) for x in 0:1 for y in 'a':'c']  # recoge generadores que involucran Iterators.flatten
6-element Vector{Tuple{Int64, Char}}:
 (0, 'a')
 (0, 'b')
 (0, 'c')
 (1, 'a')
 (1, 'b')
 (1, 'c')
```
