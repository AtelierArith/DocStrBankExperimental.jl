```
sbmv!(uplo, k, alpha, A, x, beta, y)
```

更新向量 `y` 为 `alpha*A*x + beta*y`，其中 `A` 是一个对称带状矩阵，阶数为 `size(A,2)`，具有 `k` 个超对角线，存储在参数 `A` 中。`A` 的存储布局在参考 BLAS 模块中描述，级别-2 BLAS 可在 [https://www.netlib.org/lapack/explore-html/](https://www.netlib.org/lapack/explore-html/) 找到。仅使用 [`uplo`](@ref stdlib-blas-uplo) 三角形的 `A`。

返回更新后的 `y`。
