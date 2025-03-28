```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, vl::Real, vu::Real) -> values
```

Dasselbe wie [`eigvals`](@ref), aber spart Speicherplatz, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. `vl` ist die Untergrenze des Intervalls, in dem nach Eigenwerten gesucht wird, und `vu` ist die Obergrenze.
