```
gemv!(tA, alpha, A, x, beta, y)
```

ベクトル `y` を `alpha*A*x + beta*y` または `alpha*A'x + beta*y` に更新します。これは [`tA`](@ref stdlib-blas-trans) に従います。`alpha` と `beta` はスカラーです。更新された `y` を返します。
