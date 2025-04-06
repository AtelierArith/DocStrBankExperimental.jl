```
geev!(jobvl, jobvr, A) -> (W, VL, VR)
```

Encuentra el sistema de eigenvalores de `A`. Si `jobvl = N`, los eigenvectores izquierdos de `A` no se calculan. Si `jobvr = N`, los eigenvectores derechos de `A` no se calculan. Si `jobvl = V` o `jobvr = V`, se calculan los eigenvectores correspondientes. Devuelve los eigenvalores en `W`, los eigenvectores derechos en `VR`, y los eigenvectores izquierdos en `VL`.
