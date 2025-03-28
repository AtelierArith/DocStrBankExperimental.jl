```
rank(S::SparseMatrixCSC{Tv,Ti}; [tol::Real]) -> Ti
```

Calcula el rango de `S` calculando su factorización QR. Los valores menores que `tol` se consideran cero. Consulta el manual de SPQR.
