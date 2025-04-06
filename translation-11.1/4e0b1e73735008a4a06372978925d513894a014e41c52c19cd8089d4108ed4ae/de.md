```
append!(collection, collections...) -> collection.
```

Für einen geordneten Container `collection` füge die Elemente jeder `collections` am Ende hinzu.

!!! compat "Julia 1.6"
    Das Angeben mehrerer Sammlungen, die hinzugefügt werden sollen, erfordert mindestens Julia 1.6.


# Beispiele

```jldoctest
julia> append!([1], [2, 3])
3-element Vector{Int64}:
 1
 2
 3

julia> append!([1, 2, 3], [4, 5], [6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

Verwende [`push!`](@ref), um einzelne Elemente zu `collection` hinzuzufügen, die nicht bereits in einer anderen Sammlung enthalten sind. Das Ergebnis des vorhergehenden Beispiels ist äquivalent zu `push!([1, 2, 3], 4, 5, 6)`.

Siehe [`sizehint!`](@ref) für Hinweise zum Leistungsmodell.

Siehe auch [`vcat`](@ref) für Vektoren, [`union!`](@ref) für Mengen und [`prepend!`](@ref) sowie [`pushfirst!`](@ref) für die entgegengesetzte Reihenfolge.
