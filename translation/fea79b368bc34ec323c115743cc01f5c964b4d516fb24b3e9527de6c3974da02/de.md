```
push!(collection, items...) -> collection
```

Fügen Sie ein oder mehrere `items` in `collection` ein. Wenn `collection` ein geordnetes Container ist, werden die Elemente am Ende (in der angegebenen Reihenfolge) eingefügt.

# Beispiele

```jldoctest
julia> push!([1, 2, 3], 4, 5, 6)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

Wenn `collection` geordnet ist, verwenden Sie [`append!`](@ref), um alle Elemente einer anderen Sammlung hinzuzufügen. Das Ergebnis des vorhergehenden Beispiels ist äquivalent zu `append!([1, 2, 3], [4, 5, 6])`. Für `AbstractSet`-Objekte kann stattdessen [`union!`](@ref) verwendet werden.

Siehe [`sizehint!`](@ref) für Hinweise zum Leistungsmodell.

Siehe auch [`pushfirst!`](@ref).
