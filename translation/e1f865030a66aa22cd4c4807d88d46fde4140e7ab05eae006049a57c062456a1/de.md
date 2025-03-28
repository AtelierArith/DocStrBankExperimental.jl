```
SparseArrays.spzeros!(::Type{Tv}, I, J, [m, n]) -> SparseMatrixCSC{Tv}
```

Variante von `spzeros!`, die die Eingangsvektoren `I` und `J` für die endgültige Matrixspeicherung wiederverwendet. Nach der Konstruktion werden die Eingangsvektoren die Matrixpuffer aliasieren; `S.colptr === I` und `S.rowval === J` gilt, und sie werden bei Bedarf `resize!`d.

Beachten Sie, dass einige Arbeitspuffer weiterhin zugewiesen werden. Insbesondere ist diese Methode ein praktischer Wrapper um `spzeros!(Tv, I, J, m, n, klasttouch, csrrowptr, csrcolval, csccolptr, cscrowval)`, wobei diese Methode `klasttouch`, `csrrowptr` und `csrcolval` in geeigneter Größe zuweist, aber `I` und `J` für `csccolptr` und `cscrowval` wiederverwendet.

Die Argumente `m` und `n` haben standardmäßig den Wert `maximum(I)` und `maximum(J)`.

!!! compat "Julia 1.10"
    Diese Methode erfordert Julia-Version 1.10 oder höher.

