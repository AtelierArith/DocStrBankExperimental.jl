```
SparseArrays.sparse!(I, J, V, [m, n, combine]) -> SparseMatrixCSC
```

Variante von `sparse!`, die die Eingangsvektoren (`I`, `J`, `V`) für die endgültige Matrixspeicherung wiederverwendet. Nach der Konstruktion werden die Eingangsvektoren die Matrixpuffer aliasieren; `S.colptr === I`, `S.rowval === J` und `S.nzval === V` gilt, und sie werden bei Bedarf `resize!`d.

Beachten Sie, dass einige Arbeitspuffer weiterhin zugewiesen werden. Insbesondere ist diese Methode ein praktischer Wrapper um `sparse!(I, J, V, m, n, combine, klasttouch, csrrowptr, csrcolval, csrnzval, csccolptr, cscrowval, cscnzval)`, wobei diese Methode `klasttouch`, `csrrowptr`, `csrcolval` und `csrnzval` in geeigneter Größe zuweist, aber `I`, `J` und `V` für `csccolptr`, `cscrowval` und `cscnzval` wiederverwendet.

Die Argumente `m`, `n` und `combine` haben standardmäßig die Werte `maximum(I)`, `maximum(J)` und `+`.

!!! compat "Julia 1.10"
    Diese Methode erfordert Julia-Version 1.10 oder höher.

