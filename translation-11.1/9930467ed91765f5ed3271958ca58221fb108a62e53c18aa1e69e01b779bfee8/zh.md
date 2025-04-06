```
sbmv(uplo, k, alpha, A, x)
```

返回 `alpha*A*x`，其中 `A` 是一个阶数为 `size(A,2)` 的对称带状矩阵，具有在参数 `A` 中存储的 `k` 个超对角线。仅使用 `A` 的 [`uplo`](@ref stdlib-blas-uplo) 三角部分。
