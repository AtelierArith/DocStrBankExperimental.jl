```
orglq!(A, tau, k = length(tau))
```

Encuentra explícitamente la matriz `Q` de una factorización `LQ` después de llamar a `gelqf!` en `A`. Utiliza la salida de `gelqf!`. `A` es sobrescrito por `Q`.
