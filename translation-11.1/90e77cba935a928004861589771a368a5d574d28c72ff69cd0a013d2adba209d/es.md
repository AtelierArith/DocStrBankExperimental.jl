```
haskey(collection, key) -> Bool
```

Determina si una colección tiene un mapeo para una `key` dada.

# Ejemplos

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} con 2 entradas:
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
