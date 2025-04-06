```
trunc([T,] x)
trunc(x; digits::Integer= [, basis = 10])
trunc(x; sigdigits::Integer= [, basis = 10])
```

`trunc(x)` gibt den nächstgelegenen ganzzahligen Wert des gleichen Typs wie `x` zurück, dessen absoluter Wert kleiner oder gleich dem absoluten Wert von `x` ist.

`trunc(T, x)` konvertiert das Ergebnis in den Typ `T` und wirft einen `InexactError`, wenn der truncierte Wert nicht als `T` darstellbar ist.

Die Schlüsselwörter `digits`, `sigdigits` und `basis` funktionieren wie bei [`round`](@ref).

Um `trunc` für einen neuen Typ zu unterstützen, definiere `Base.round(x::NewType, ::RoundingMode{:ToZero})`.

Siehe auch: [`%`](@ref rem), [`floor`](@ref), [`unsigned`](@ref), [`unsafe_trunc`](@ref).

# Beispiele

```jldoctest
julia> trunc(2.22)
2.0

julia> trunc(-2.22, digits=1)
-2.2

julia> trunc(Int, -2.22)
-2
```
