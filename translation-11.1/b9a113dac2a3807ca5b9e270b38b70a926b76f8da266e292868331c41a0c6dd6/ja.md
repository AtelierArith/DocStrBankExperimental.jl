```
syr!(uplo, alpha, x, A)
```

ベクトル `x` を用いた対称行列 `A` のランク1更新を行います。更新は `alpha*x*transpose(x) + A` です。[`uplo`](@ref stdlib-blas-uplo) は更新される `A` の三角形を制御します。`A` を返します。
