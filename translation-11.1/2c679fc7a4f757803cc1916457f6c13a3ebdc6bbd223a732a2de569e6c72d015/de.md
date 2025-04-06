```
deleteat!(a::Vector, inds)
```

Entfernt die Elemente an den durch `inds` angegebenen Indizes und gibt das modifizierte `a` zurück. Nachfolgende Elemente werden verschoben, um die resultierende Lücke zu füllen.

`inds` kann entweder ein Iterator oder eine Sammlung von sortierten und einzigartigen Ganzzahlindizes oder ein boolescher Vektor der gleichen Länge wie `a` sein, wobei `true` Einträge anzeigt, die gelöscht werden sollen.

# Beispiele

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], [true, false, true, false, true, false])
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], (2, 2))
ERROR: ArgumentError: indices must be unique and sorted
Stacktrace:
[...]
```
