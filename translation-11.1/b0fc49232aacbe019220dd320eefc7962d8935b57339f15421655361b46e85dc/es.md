```
ggev!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

Encuentra la descomposición de eigen generalizada de `A` y `B`. Si `jobvl = N`, los eigenvectores izquierdos no se calculan. Si `jobvr = N`, los eigenvectores derechos no se calculan. Si `jobvl = V` o `jobvr = V`, se calculan los eigenvectores correspondientes.
