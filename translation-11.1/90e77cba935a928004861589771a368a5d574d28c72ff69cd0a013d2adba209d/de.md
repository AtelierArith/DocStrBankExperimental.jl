```
haskey(collection, key) -> Bool
```

Bestimmen Sie, ob eine Sammlung eine Zuordnung für einen gegebenen `key` hat.

# Beispiele

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} mit 2 Einträgen:
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
