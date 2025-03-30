```
gemm!(tA, tB, alpha, A, B, beta, C)
```

`C`'yi `alpha*A*B + beta*C` veya [`tA`](@ref stdlib-blas-trans) ve `tB`'ye göre diğer üç varyantla güncelleyin. Güncellenmiş `C`'yi döndürün.
