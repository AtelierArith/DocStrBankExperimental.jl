```
values(iterator)
```

Für einen Iterator oder eine Sammlung, die Schlüssel und Werte hat, gibt es einen Iterator über die Werte zurück. Diese Funktion gibt standardmäßig einfach ihr Argument zurück, da die Elemente eines allgemeinen Iterators normalerweise als seine "Werte" betrachtet werden.

# Beispiele

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> values(d)
ValueIterator für ein Dict{String, Int64} mit 2 Einträgen. Werte:
  2
  1

julia> values([2])
1-element Vector{Int64}:
 2
```
