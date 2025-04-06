```
gbtrf!(kl, ku, m, AB) -> (AB, ipiv)
```

Calcula la factorización LU de una matriz en banda `AB`. `kl` es la primera subdiagonal que contiene una banda no nula, `ku` es la última superdiagonal que contiene una, y `m` es la primera dimensión de la matriz `AB`. Devuelve la factorización LU en su lugar y `ipiv`, el vector de pivotes utilizados.
