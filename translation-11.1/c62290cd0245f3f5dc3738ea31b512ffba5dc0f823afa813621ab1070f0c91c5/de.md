```
supertypes(T::Type)
```

Gibt ein Tupel `(T, ..., Any)` von `T` und all seinen Supertypen zurück, wie durch aufeinanderfolgende Aufrufe der [`supertype`](@ref) Funktion bestimmt, aufgelistet in der Reihenfolge von `<:` und beendet mit `Any`.

Siehe auch [`subtypes`](@ref).

# Beispiele

```jldoctest
julia> supertypes(Int)
(Int64, Signed, Integer, Real, Number, Any)
```
