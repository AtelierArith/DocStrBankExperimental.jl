```
Dict([itr])
```

`Dict{K,V}()` konstruiert eine Hash-Tabelle mit Schlüsseln vom Typ `K` und Werten vom Typ `V`. Schlüssel werden mit [`isequal`](@ref) verglichen und mit [`hash`](@ref) gehasht.

Bei einem einzelnen iterierbaren Argument wird ein [`Dict`](@ref) konstruiert, dessen Schlüssel-Wert-Paare aus 2-Tupeln `(key,value)` stammen, die vom Argument erzeugt werden.

# Beispiele

```jldoctest
julia> Dict([("A", 1), ("B", 2)])
Dict{String, Int64} mit 2 Einträgen:
  "B" => 2
  "A" => 1
```

Alternativ kann eine Sequenz von Paar-Argumenten übergeben werden.

```jldoctest
julia> Dict("A"=>1, "B"=>2)
Dict{String, Int64} mit 2 Einträgen:
  "B" => 2
  "A" => 1
```

!!! warning
    Schlüssel dürfen veränderlich sein, aber wenn Sie gespeicherte Schlüssel ändern, kann die Hash-Tabelle intern inkonsistent werden, in diesem Fall funktioniert das `Dict` möglicherweise nicht richtig. [`IdDict`](@ref) kann eine Alternative sein, wenn Sie Schlüssel ändern müssen.

