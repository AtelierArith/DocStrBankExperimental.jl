```
ggev3!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

Encuentra la descomposición generalizada de eigen de `A` y `B` utilizando un algoritmo bloqueado. Si `jobvl = N`, los eigenvectores izquierdos no se calculan. Si `jobvr = N`, los eigenvectores derechos no se calculan. Si `jobvl = V` o `jobvr = V`, se calculan los eigenvectores correspondientes. Esta función requiere LAPACK 3.6.0.
