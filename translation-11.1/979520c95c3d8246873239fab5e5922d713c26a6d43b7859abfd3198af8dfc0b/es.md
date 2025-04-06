```
empty!(collection) -> collection
```

Elimina todos los elementos de una `collection`.

# Ejemplos

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} con 2 entradas:
  "b" => 2
  "a" => 1

julia> empty!(A);

julia> A
Dict{String, Int64}()
```
