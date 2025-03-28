```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> Eigen
```

Berechnet die Eigenwertzerlegung von `A` und gibt ein [`Eigen`](@ref) Faktorisierungsobjekt `F` zurück, das die Eigenwerte in `F.values` und die Eigenvektoren in den Spalten der Matrix `F.vectors` enthält. (Der `k`-te Eigenvektor kann aus dem Slice `F.vectors[:, k]` abgerufen werden.)

Das Iterieren über die Zerlegung erzeugt die Komponenten `F.values` und `F.vectors`.

Die folgenden Funktionen sind für `Eigen`-Objekte verfügbar: [`inv`](@ref), [`det`](@ref) und [`isposdef`](@ref).

Der [`UnitRange`](@ref) `irange` gibt die Indizes der sortierten Eigenwerte an, nach denen gesucht werden soll.

!!! Hinweis     Wenn `irange` nicht `1:n` ist, wobei `n` die Dimension von `A` ist, wird die zurückgegebene Faktorisierung eine *trunkierte* Faktorisierung sein.
