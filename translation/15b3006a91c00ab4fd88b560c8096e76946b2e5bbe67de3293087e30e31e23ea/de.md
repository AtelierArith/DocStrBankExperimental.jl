```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, vl::Real, vu::Real) -> Eigen
```

Berechnet die Eigenwertzerlegung von `A` und gibt ein [`Eigen`](@ref) Faktorisierungsobjekt `F` zurück, das die Eigenwerte in `F.values` und die Eigenvektoren in den Spalten der Matrix `F.vectors` enthält. (Der `k`-te Eigenvektor kann aus dem Slice `F.vectors[:, k]` abgerufen werden.)

Das Iterieren über die Zerlegung produziert die Komponenten `F.values` und `F.vectors`.

Die folgenden Funktionen sind für `Eigen`-Objekte verfügbar: [`inv`](@ref), [`det`](@ref) und [`isposdef`](@ref).

`vl` ist die untere Grenze des Fensters von Eigenwerten, nach denen gesucht werden soll, und `vu` ist die obere Grenze.

!!! note
    Wenn [`vl`, `vu`] nicht alle Eigenwerte von `A` enthält, wird die zurückgegebene Faktorisierung eine *trunkierte* Faktorisierung sein.

