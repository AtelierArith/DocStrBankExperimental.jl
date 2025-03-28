```
∉(item, collection) -> Bool
∌(collection, item) -> Bool
```

Negation von `∈` und `∋`, d.h. überprüft, dass `item` nicht in `collection` ist.

Beim Broadcasting mit `items .∉ collection` werden sowohl `item` als auch `collection` überbroadcastet, was oft nicht beabsichtigt ist. Wenn beide Argumente Vektoren sind (und die Dimensionen übereinstimmen), ist das Ergebnis ein Vektor, der angibt, ob jeder Wert in der Sammlung `items` nicht im Wert an der entsprechenden Position in `collection` ist. Um einen Vektor zu erhalten, der angibt, ob jeder Wert in `items` nicht in `collection` ist, wickeln Sie `collection` in ein Tupel oder ein `Ref` wie folgt: `items .∉ Ref(collection)`.

# Beispiele

```jldoctest
julia> 1 ∉ 2:4
true

julia> 1 ∉ 1:3
false

julia> [1, 2] .∉ [2, 3]
2-element BitVector:
 1
 1

julia> [1, 2] .∉ ([2, 3],)
2-element BitVector:
 1
 0
```
