```
Base.split_rest(collection, n::Int[, itr_state]) -> (rest_but_n, last_n)
```

Generische Funktion zum Teilen des Endes von `collection`, beginnend von einem bestimmten Iterationszustand `itr_state`. Gibt ein Tupel von zwei neuen Sammlungen zurück. Die erste enthält alle Elemente des Endes, außer den `n` letzten, die die zweite Sammlung bilden.

Der Typ der ersten Sammlung folgt im Allgemeinen dem von [`Base.rest`](@ref), mit der Ausnahme, dass der Fallback-Fall nicht faul ist, sondern eifrig in einen Vektor gesammelt wird.

Kann für benutzerdefinierte Sammlungstypen überladen werden, um das Verhalten von [slurping in assignments](@ref destructuring-assignment) in nicht-finaler Position anzupassen, wie `a, b..., c = collection`.

!!! compat "Julia 1.9"
    `Base.split_rest` erfordert mindestens Julia 1.9.


Siehe auch: [`Base.rest`](@ref).

# Beispiele

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.split_rest(a, 1, state)
(1, ([3, 2], [4]))
```
