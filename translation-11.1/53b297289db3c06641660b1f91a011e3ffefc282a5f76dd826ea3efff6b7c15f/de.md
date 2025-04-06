```
Base.rest(collection[, itr_state])
```

Generische Funktion zum Abrufen des Endes von `collection`, beginnend von einem bestimmten Iterationszustand `itr_state`. Gibt ein `Tuple` zurück, wenn `collection` selbst ein `Tuple` ist, einen Untertyp von `AbstractVector`, wenn `collection` ein `AbstractArray` ist, einen Untertyp von `AbstractString`, wenn `collection` ein `AbstractString` ist, und einen beliebigen Iterator, der andernfalls auf `Iterators.rest(collection[, itr_state])` zurückfällt.

Kann für benutzerdefinierte Sammlungstypen überladen werden, um das Verhalten von [slurping in assignments](@ref destructuring-assignment) in der letzten Position anzupassen, wie `a, b... = collection`.

!!! compat "Julia 1.6"
    `Base.rest` erfordert mindestens Julia 1.6.


Siehe auch: [`first`](@ref first), [`Iterators.rest`](@ref), [`Base.split_rest`](@ref).

# Beispiele

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.rest(a, state)
(1, [3, 2, 4])
```
