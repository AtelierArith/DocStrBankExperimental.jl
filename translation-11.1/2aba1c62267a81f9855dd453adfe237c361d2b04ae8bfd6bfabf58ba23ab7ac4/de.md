```
potri!(uplo, A)
```

Berechnet die Inverse der positiv definiten Matrix `A`, nachdem `potrf!` aufgerufen wurde, um ihre (obere, wenn `uplo = U`, untere, wenn `uplo = L`) Cholesky-Zerlegung zu finden.

`A` wird durch seine Inverse überschrieben und zurückgegeben.
