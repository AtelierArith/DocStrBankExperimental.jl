```
stev!(job, dv, ev) -> (dv, Zmat)
```

Calcula el sistema de eigenvalores para una matriz tridiagonal simétrica con `dv` como diagonal y `ev` como subdiagonal. Si `job = N`, solo se encuentran y devuelven los eigenvalores en `dv`. Si `job = V`, entonces también se encuentran y devuelven los eigenvectores en `Zmat`.
