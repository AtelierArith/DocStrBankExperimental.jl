```
orgqr!(A, tau, k = length(tau))
```

Encuentra explícitamente la matriz `Q` de una factorización `QR` después de llamar a `geqrf!` en `A`. Utiliza la salida de `geqrf!`. `A` se sobrescribe con `Q`.
