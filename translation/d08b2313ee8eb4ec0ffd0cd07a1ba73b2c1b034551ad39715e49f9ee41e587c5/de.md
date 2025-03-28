```
stride(A, k::Integer)
```

Gibt den Abstand im Speicher (in Anzahl der Elemente) zwischen benachbarten Elementen in der Dimension `k` zurück.

Siehe auch: [`strides`](@ref).

# Beispiele

```jldoctest
julia> A = fill(1, (3,4,5));

julia> stride(A,2)
3

julia> stride(A,3)
12
```
