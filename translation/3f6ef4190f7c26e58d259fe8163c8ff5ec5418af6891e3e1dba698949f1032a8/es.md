```
gemm!(tA, tB, alpha, A, B, beta, C)
```

Actualiza `C` como `alpha*A*B + beta*C` o las otras tres variantes según [`tA`](@ref stdlib-blas-trans) y `tB`. Devuelve el `C` actualizado.
