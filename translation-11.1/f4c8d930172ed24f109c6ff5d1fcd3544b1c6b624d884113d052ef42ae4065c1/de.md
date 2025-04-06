```
posv!(uplo, A, B) -> (A, B)
```

Findet die Lösung von `A * X = B`, wobei `A` eine symmetrische oder hermitesche positiv definite Matrix ist. Wenn `uplo = U`, wird die obere Cholesky-Zerlegung von `A` berechnet. Wenn `uplo = L`, wird die untere Cholesky-Zerlegung von `A` berechnet. `A` wird durch seine Cholesky-Zerlegung überschrieben. `B` wird mit der Lösung `X` überschrieben.
