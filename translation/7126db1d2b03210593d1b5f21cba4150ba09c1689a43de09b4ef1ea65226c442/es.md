```
trtri!(uplo, diag, A)
```

Encuentra la inversa de la matriz triangular (superior si `uplo = U`, inferior si `uplo = L`) `A`. Si `diag = N`, `A` tiene elementos diagonales no unitarios. Si `diag = U`, todos los elementos diagonales de `A` son uno. `A` se sobrescribe con su inversa.
