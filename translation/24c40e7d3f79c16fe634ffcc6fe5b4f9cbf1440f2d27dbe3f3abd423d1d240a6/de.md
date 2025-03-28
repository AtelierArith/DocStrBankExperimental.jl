```
adjoint!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

Transponiere die Matrix `A` und speichere den Adjungierten der Elemente in der Matrix `X`. `size(X)` muss gleich `size(transpose(A))` sein. Es wird kein zusätzlicher Speicher zugewiesen, außer wenn die Zeilenwerte und nzval von `X` bei Bedarf angepasst werden.

Siehe `halfperm!`
