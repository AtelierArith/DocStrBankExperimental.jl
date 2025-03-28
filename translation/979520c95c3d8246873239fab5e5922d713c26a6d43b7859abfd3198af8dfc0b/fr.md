```
empty!(collection) -> collection
```

Supprime tous les éléments d'une `collection`.

# Exemples

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} avec 2 entrées :
  "b" => 2
  "a" => 1

julia> empty!(A);

julia> A
Dict{String, Int64}()
```
