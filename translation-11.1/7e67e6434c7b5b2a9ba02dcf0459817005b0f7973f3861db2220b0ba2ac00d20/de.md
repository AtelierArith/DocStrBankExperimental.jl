```
Pair(x, y)
x => y
```

Konstruiere ein `Pair`-Objekt mit dem Typ `Pair{typeof(x), typeof(y)}`. Die Elemente werden in den Feldern `first` und `second` gespeichert. Sie können auch über Iteration zugegriffen werden (aber ein `Pair` wird für Broadcast-Operationen als ein einzelner "Skalar" behandelt).

Siehe auch [`Dict`](@ref).

# Beispiele

```jldoctest
julia> p = "foo" => 7
"foo" => 7

julia> typeof(p)
Pair{String, Int64}

julia> p.first
"foo"

julia> for x in p
           println(x)
       end
foo
7

julia> replace.(["xops", "oxps"], "x" => "o")
2-element Vector{String}:
 "oops"
 "oops"
```
