```
in(item, collection) -> Bool
∈(item, collection) -> Bool
```

Bestimmen Sie, ob ein Element in der gegebenen Sammlung enthalten ist, im Sinne, dass es [`==`](@ref) zu einem der Werte ist, die durch Iteration über die Sammlung erzeugt werden. Gibt einen `Bool`-Wert zurück, es sei denn, `item` ist [`missing`](@ref) oder `collection` enthält `missing`, aber nicht `item`, in diesem Fall wird `missing` zurückgegeben ([dreiwertige Logik](https://de.wikipedia.org/wiki/Dreiwertige_Logik), die dem Verhalten von [`any`](@ref) und [`==`](@ref) entspricht).

Einige Sammlungen folgen einer leicht anderen Definition. Zum Beispiel überprüfen [`Set`](@ref)s, ob das Element [`isequal`](@ref) zu einem der Elemente ist; [`Dict`](@ref)s suchen nach `key=>value`-Paaren, und der `key` wird mit [`isequal`](@ref) verglichen.

Um das Vorhandensein eines Schlüssels in einem Wörterbuch zu testen, verwenden Sie [`haskey`](@ref) oder `k in keys(dict)`. Für die oben genannten Sammlungen ist das Ergebnis immer ein `Bool`.

Beim Broadcasting mit `in.(items, collection)` oder `items .∈ collection` werden sowohl `item` als auch `collection` über die Elemente gebroadcastet, was oft nicht beabsichtigt ist. Wenn beide Argumente Vektoren sind (und die Dimensionen übereinstimmen), ist das Ergebnis ein Vektor, der angibt, ob jeder Wert in der Sammlung `items` im Wert an der entsprechenden Position in `collection` enthalten ist. Um einen Vektor zu erhalten, der angibt, ob jeder Wert in `items` in `collection` enthalten ist, wickeln Sie `collection` in ein Tupel oder ein `Ref` wie folgt ein: `in.(items, Ref(collection))` oder `items .∈ Ref(collection)`.

Siehe auch: [`∉`](@ref), [`insorted`](@ref), [`contains`](@ref), [`occursin`](@ref), [`issubset`](@ref).

# Beispiele

```jldoctest
julia> a = 1:3:20
1:3:19

julia> 4 in a
true

julia> 5 in a
false

julia> missing in [1, 2]
missing

julia> 1 in [2, missing]
missing

julia> 1 in [1, missing]
true

julia> missing in Set([1, 2])
false

julia> (1=>missing) in Dict(1=>10, 2=>20)
missing

julia> [1, 2] .∈ [2, 3]
2-element BitVector:
 0
 0

julia> [1, 2] .∈ ([2, 3],)
2-element BitVector:
 0
 1
```
