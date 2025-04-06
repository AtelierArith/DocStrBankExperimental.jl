```
strides(A)
```

Gibt ein Tupel der Speicherstrides in jeder Dimension zurück.

Siehe auch: [`stride`](@ref).

# Beispiele

```jldoctest
julia> A = fill(1, (3,4,5));

julia> strides(A)
(1, 3, 12)
```
