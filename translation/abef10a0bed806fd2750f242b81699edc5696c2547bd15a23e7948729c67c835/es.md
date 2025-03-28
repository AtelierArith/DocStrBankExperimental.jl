```
ormrz!(lado, trans, A, tau, C)
```

Multiplica la matriz `C` por `Q` de la transformación suministrada por `tzrzf!`. Dependiendo de `lado` o `trans`, la multiplicación puede ser del lado izquierdo (`lado = L, Q*C`) o del lado derecho (`lado = R, C*Q`) y `Q` puede estar sin modificar (`trans = N`), transpuesta (`trans = T`), o conjugadamente transpuesta (`trans = C`). Devuelve la matriz `C` que se modifica en su lugar con el resultado de la multiplicación.
