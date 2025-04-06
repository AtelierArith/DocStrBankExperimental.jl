```
to_indices(A, I::Tuple)
```

Konvertiere das Tupel `I` in ein Tupel von Indizes zur Verwendung beim Indizieren des Arrays `A`.

Das zurückgegebene Tupel darf nur `Int`s oder `AbstractArray`s von Skalarindizes enthalten, die von Array `A` unterstützt werden. Es wird einen Fehler auslösen, wenn es auf einen neuartigen Indextyp stößt, den es nicht verarbeiten kann.

Für einfache Indextypen wird auf die nicht exportierte Funktion `Base.to_index(A, i)` verwiesen, um jeden Index `i` zu verarbeiten. Während diese interne Funktion nicht direkt aufgerufen werden soll, kann `Base.to_index` von benutzerdefinierten Array- oder Indextypen erweitert werden, um benutzerdefinierte Indizierungsverhalten bereitzustellen.

Kompliziertere Indextypen benötigen möglicherweise mehr Kontext über die Dimension, in die sie indizieren. Um diese Fälle zu unterstützen, ruft `to_indices(A, I)` `to_indices(A, axes(A), I)` auf, das dann rekursiv sowohl durch das gegebene Tupel von Indizes als auch durch die dimensionalen Indizes von `A` in Tandem geht. Daher ist nicht garantiert, dass alle Indextypen zu `Base.to_index` weitergeleitet werden.

# Beispiele

```jldoctest
julia> A = zeros(1,2,3,4);

julia> to_indices(A, (1,1,2,2))
(1, 1, 2, 2)

julia> to_indices(A, (1,1,2,20)) # keine Grenzüberprüfung
(1, 1, 2, 20)

julia> to_indices(A, (CartesianIndex((1,)), 2, CartesianIndex((3,4)))) # exotischer Index
(1, 2, 3, 4)

julia> to_indices(A, ([1,1], 1:2, 3, 4))
([1, 1], 1:2, 3, 4)

julia> to_indices(A, (1,2)) # keine Formüberprüfung
(1, 2)
```
