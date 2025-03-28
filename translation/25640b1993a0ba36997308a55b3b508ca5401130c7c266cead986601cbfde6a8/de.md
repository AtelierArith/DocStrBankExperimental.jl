```
sparsevec(d::Dict, [m])
```

Erstellt einen spärlichen Vektor der Länge `m`, wobei die Nicht-Null-Indizes Schlüssel aus dem Wörterbuch sind und die Nicht-Null-Werte die Werte aus dem Wörterbuch sind.

# Beispiele

```jldoctest
julia> sparsevec(Dict(1 => 3, 2 => 2))
2-element SparseVector{Int64, Int64} with 2 stored entries:
  [1]  =  3
  [2]  =  2
```
