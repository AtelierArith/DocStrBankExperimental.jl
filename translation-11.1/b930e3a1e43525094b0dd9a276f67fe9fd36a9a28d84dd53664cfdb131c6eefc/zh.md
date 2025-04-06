```
gbmv!(trans, m, kl, ku, alpha, A, x, beta, y)
```

根据 [`trans`](@ref stdlib-blas-trans) 更新向量 `y` 为 `alpha*A*x + beta*y` 或 `alpha*A'*x + beta*y`。矩阵 `A` 是一个维度为 `m` x `size(A,2)` 的一般带状矩阵，具有 `kl` 个下对角线和 `ku` 个上对角线。`alpha` 和 `beta` 是标量。返回更新后的 `y`。
