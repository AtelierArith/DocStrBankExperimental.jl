```
bdsqr!(uplo, d, e_, Vt, U, C) -> (d, Vt, U, C)
```

Calcula la descomposición en valores singulares de una matriz bidiagonal con `d` en la diagonal y `e_` en la subdiagonal. Si `uplo = U`, `e_` es la superdiagonal. Si `uplo = L`, `e_` es la subdiagonal. También se puede calcular opcionalmente el producto `Q' * C`.

Devuelve los valores singulares en `d`, y la matriz `C` sobrescrita con `Q' * C`.
