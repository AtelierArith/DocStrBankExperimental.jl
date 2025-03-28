```
transpose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

Transponiere die Matrix `A` und speichere sie in der Matrix `X`. `size(X)` muss gleich `size(transpose(A))` sein. Es wird kein zusätzlicher Speicher zugewiesen, außer wenn die `rowval` und `nzval` von `X` bei Bedarf angepasst werden.

Siehe `halfperm!`
