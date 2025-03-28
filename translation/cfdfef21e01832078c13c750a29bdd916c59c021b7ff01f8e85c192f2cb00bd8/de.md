```
ceil([T,] x)
ceil(x; digits::Integer= [, basis = 10])
ceil(x; sigdigits::Integer= [, basis = 10])
```

`ceil(x)` gibt den nächstgelegenen ganzzahligen Wert des gleichen Typs wie `x` zurück, der größer oder gleich `x` ist.

`ceil(T, x)` konvertiert das Ergebnis in den Typ `T` und wirft einen `InexactError`, wenn der gerundete Wert nicht als `T` darstellbar ist.

Die Schlüsselwörter `digits`, `sigdigits` und `basis` funktionieren wie bei [`round`](@ref).

Um `ceil` für einen neuen Typ zu unterstützen, definiere `Base.round(x::NewType, ::RoundingMode{:Up})`.
