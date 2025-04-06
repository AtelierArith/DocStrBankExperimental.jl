```
ndims(A::AbstractArray) -> Integer
```

Gibt die Anzahl der Dimensionen von `A` zurück.

Siehe auch: [`size`](@ref), [`axes`](@ref).

# Beispiele

```jldoctest
julia> A = fill(1, (3,4,5));

julia> ndims(A)
3
```
