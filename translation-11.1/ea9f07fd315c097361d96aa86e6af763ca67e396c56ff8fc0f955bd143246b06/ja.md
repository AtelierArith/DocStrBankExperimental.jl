```
her!(uplo, alpha, x, A)
```

複素配列専用のメソッド。ベクトル `x` を用いたエルミート行列 `A` のランク1更新 `alpha*x*x' + A` を行います。[`uplo`](@ref stdlib-blas-uplo) は、更新される `A` の三角形を制御します。`A` を返します。
