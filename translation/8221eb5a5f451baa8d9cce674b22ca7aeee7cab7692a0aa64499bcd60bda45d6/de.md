```
potrs!(uplo, A, B)
```

Findet die Lösung zu `A * X = B`, wobei `A` eine symmetrische oder hermitische positiv definite Matrix ist, deren Cholesky-Zerlegung mit `potrf!` berechnet wurde. Wenn `uplo = U`, wurde die obere Cholesky-Zerlegung von `A` berechnet. Wenn `uplo = L`, wurde die untere Cholesky-Zerlegung von `A` berechnet. `B` wird mit der Lösung `X` überschrieben.
