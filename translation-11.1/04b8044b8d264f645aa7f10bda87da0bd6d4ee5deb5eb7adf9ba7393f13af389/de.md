```
values(a::AbstractDict)
```

Gibt einen Iterator über alle Werte in einer Sammlung zurück. `collect(values(a))` gibt ein Array von Werten zurück. Wenn die Werte intern in einer Hash-Tabelle gespeichert sind, wie es bei `Dict` der Fall ist, kann die Reihenfolge, in der sie zurückgegeben werden, variieren. Aber `keys(a)`, `values(a)` und `pairs(a)` iterieren alle `a` und geben die Elemente in derselben Reihenfolge zurück.

# Beispiele

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} mit 2 Einträgen:
  'a' => 2
  'b' => 3

julia> collect(values(D))
2-element Vector{Int64}:
 2
 3
```
