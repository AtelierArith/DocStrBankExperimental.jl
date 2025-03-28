```
empty!(collection) -> collection
```

Entfernt alle Elemente aus einer `collection`.

# Beispiele

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} mit 2 Einträgen:
  "b" => 2
  "a" => 1

julia> empty!(A);

julia> A
Dict{String, Int64}()
```
