```
ntuple(f, n::Integer)
```

Erstellt ein Tupel der Länge `n`, wobei jedes Element als `f(i)` berechnet wird, wobei `i` der Index des Elements ist.

# Beispiele

```jldoctest
julia> ntuple(i -> 2*i, 4)
(2, 4, 6, 8)
```
