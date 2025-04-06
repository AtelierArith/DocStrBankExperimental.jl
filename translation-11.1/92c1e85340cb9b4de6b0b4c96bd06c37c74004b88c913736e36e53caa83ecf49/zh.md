```
lowrankupdate(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

使用向量 `v` 更新 Cholesky 分解 `C`。如果 `A = C.U'C.U`，则 `CC = cholesky(C.U'C.U + v*v')`，但 `CC` 的计算仅使用 `O(n^2)` 操作。
