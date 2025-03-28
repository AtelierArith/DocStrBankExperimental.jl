```
floor([T,] x)
floor(x; digits::Integer= [, basis = 10])
floor(x; sigdigits::Integer= [, basis = 10])
```

`floor(x)` gibt den nächstgelegenen ganzzahligen Wert des gleichen Typs wie `x` zurück, der kleiner oder gleich `x` ist.

`floor(T, x)` konvertiert das Ergebnis in den Typ `T` und wirft einen `InexactError`, wenn der gerundete Wert nicht als `T` darstellbar ist.

Die Schlüsselwörter `digits`, `sigdigits` und `basis` funktionieren wie bei [`round`](@ref).

Um `floor` für einen neuen Typ zu unterstützen, definiere `Base.round(x::NewType, ::RoundingMode{:Down})`.
