```
gbtrs!(trans, kl, ku, m, AB, ipiv, B)
```

Resuelve la ecuación `AB * X = B`. `trans` determina la orientación de `AB`. Puede ser `N` (sin transponer), `T` (transponer) o `C` (transposición conjugada). `kl` es la primera subdiagonal que contiene una banda no nula, `ku` es la última superdiagonal que contiene una, y `m` es la primera dimensión de la matriz `AB`. `ipiv` es el vector de pivotes devuelto por `gbtrf!`. Devuelve el vector o matriz `X`, sobrescribiendo `B` en su lugar.
