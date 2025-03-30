```
gbmv(trans, m, kl, ku, alpha, A, x)
```

根据 [`trans`](@ref stdlib-blas-trans) 返回 `alpha*A*x` 或 `alpha*A'*x`。矩阵 `A` 是一个维度为 `m` 乘 `size(A,2)` 的一般带状矩阵，具有 `kl` 个下对角线和 `ku` 个上对角线，`alpha` 是一个标量。
