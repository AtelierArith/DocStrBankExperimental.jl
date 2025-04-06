```
haskey(collection, key) -> Bool
```

Déterminez si une collection a une correspondance pour une `key` donnée.

# Exemples

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} avec 2 entrées :
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
