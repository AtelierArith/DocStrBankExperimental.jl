```
sytri!(uplo, A, ipiv)
```

Calcula la inversa de una matriz simétrica `A` utilizando los resultados de `sytrf!`. Si `uplo = U`, se almacena la mitad superior de `A`. Si `uplo = L`, se almacena la mitad inferior. `A` se sobrescribe con su inversa.
