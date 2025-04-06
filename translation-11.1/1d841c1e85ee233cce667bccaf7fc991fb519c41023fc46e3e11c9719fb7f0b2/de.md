```
pairs(collection)
```

Gibt einen Iterator über `key => value` Paare für jede Sammlung zurück, die eine Menge von Schlüsseln einer Menge von Werten zuordnet. Dazu gehören Arrays, bei denen die Schlüssel die Array-Indizes sind. Wenn die Einträge intern in einer Hash-Tabelle gespeichert sind, wie es bei `Dict` der Fall ist, kann die Reihenfolge, in der sie zurückgegeben werden, variieren. Aber `keys(a)`, `values(a)` und `pairs(a)` iterieren alle über `a` und geben die Elemente in derselben Reihenfolge zurück.

# Beispiele

```jldoctest
julia> a = Dict(zip(["a", "b", "c"], [1, 2, 3]))
Dict{String, Int64} mit 3 Einträgen:
  "c" => 3
  "b" => 2
  "a" => 1

julia> pairs(a)
Dict{String, Int64} mit 3 Einträgen:
  "c" => 3
  "b" => 2
  "a" => 1

julia> foreach(println, pairs(["a", "b", "c"]))
1 => "a"
2 => "b"
3 => "c"

julia> (;a=1, b=2, c=3) |> pairs |> collect
3-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
 :c => 3

julia> (;a=1, b=2, c=3) |> collect
3-element Vector{Int64}:
 1
 2
 3
```
