```
lowrankupdate!(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

使用向量 `v` 更新 Cholesky 分解 `C`。如果 `A = C.U'C.U`，则 `CC = cholesky(C.U'C.U + v*v')`，但 `CC` 的计算仅使用 `O(n^2)` 操作。输入的分解 `C` 会就地更新，以便在退出时 `C == CC`。在计算过程中，向量 `v` 会被销毁。
