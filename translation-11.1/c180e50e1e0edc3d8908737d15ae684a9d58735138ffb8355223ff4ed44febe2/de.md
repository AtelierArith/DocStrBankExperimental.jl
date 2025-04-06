```
ftranspose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}, f::Function) where {Tv,Ti}
```

Transponiere `A` und speichere es in `X`, während die Funktion `f` auf die Nicht-Null-Elemente angewendet wird. Entfernt nicht die Nullen, die durch `f` erzeugt werden. `size(X)` muss gleich `size(transpose(A))` sein. Es wird kein zusätzlicher Speicher zugewiesen, außer wenn die `rowval` und `nzval` von `X` bei Bedarf geändert werden.

Siehe `halfperm!`
