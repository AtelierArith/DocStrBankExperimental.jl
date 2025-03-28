```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

Gleich wie [`eigvals`](@ref), aber spart Speicherplatz, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. `irange` ist ein Bereich von Eigenwert *Indizes*, nach denen gesucht werden soll - zum Beispiel die 2. bis 8. Eigenwerte.
