```
partition(colección, n)
```

Iterar sobre una colección `n` elementos a la vez.

# Ejemplos

```jldoctest
julia> collect(Iterators.partition([1,2,3,4,5], 2))
3-element Vector{SubArray{Int64, 1, Vector{Int64}, Tuple{UnitRange{Int64}}, true}}:
 [1, 2]
 [3, 4]
 [5]
```
