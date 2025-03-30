```
rank(S::SparseMatrixCSC{Tv,Ti}; [tol::Real]) -> Ti
```

通过计算 `S` 的 QR 分解来计算秩。小于 `tol` 的值被视为零。请参阅 SPQR 的手册。
