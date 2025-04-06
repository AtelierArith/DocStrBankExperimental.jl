```
isempty(collection) -> Bool
```

Bestimmen Sie, ob eine Sammlung leer ist (keine Elemente hat).

!!! warning
    `isempty(itr)` kann das nächste Element eines zustandsbehafteten Iterators `itr` konsumieren, es sei denn, eine geeignete [`Base.isdone(itr)`](@ref) Methode ist definiert. Zustandsbehaftete Iteratoren *sollten* `isdone` implementieren, aber Sie möchten möglicherweise die Verwendung von `isempty` vermeiden, wenn Sie generischen Code schreiben, der jeden Iterator-Typ unterstützen sollte.


# Beispiele

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
