```
pushfirst!(collection, items...) -> collection
```

Fügen Sie ein oder mehrere `items` am Anfang von `collection` ein.

Diese Funktion wird in vielen anderen Programmiersprachen `unshift` genannt.

# Beispiele

```jldoctest
julia> pushfirst!([1, 2, 3, 4], 5, 6)
6-element Vector{Int64}:
 5
 6
 1
 2
 3
 4
```
