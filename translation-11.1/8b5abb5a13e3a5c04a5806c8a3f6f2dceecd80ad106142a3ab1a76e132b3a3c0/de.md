```
collect(element_type, collection)
```

Gibt ein `Array` mit dem angegebenen Elementtyp aller Elemente in einer Sammlung oder iterierbaren Struktur zurück. Das Ergebnis hat die gleiche Form und Anzahl der Dimensionen wie `collection`.

# Beispiele

```jldoctest
julia> collect(Float64, 1:2:5)
3-element Vector{Float64}:
 1.0
 3.0
 5.0
```
