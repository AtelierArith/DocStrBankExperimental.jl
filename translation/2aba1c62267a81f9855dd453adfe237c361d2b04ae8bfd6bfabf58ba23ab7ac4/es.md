```
potri!(uplo, A)
```

Calcula la inversa de la matriz definida positiva `A` después de llamar a `potrf!` para encontrar su descomposición de Cholesky (superior si `uplo = U`, inferior si `uplo = L`).

`A` se sobrescribe con su inversa y se devuelve.
