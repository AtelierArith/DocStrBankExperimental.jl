```
sbmv(uplo, k, alpha, A, x)
```

`α*A*x`を返します。ここで、`A`は引数`A`に格納された`k`個の上対角線を持つ対称バンド行列で、順序は`size(A,2)`です。`A`の[`uplo`](@ref stdlib-blas-uplo)三角形のみが使用されます。
