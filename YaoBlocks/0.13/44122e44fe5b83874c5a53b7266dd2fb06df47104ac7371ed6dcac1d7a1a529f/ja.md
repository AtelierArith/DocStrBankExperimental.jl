```
GeneralMatrixBlock{D, MT} <: PrimitiveBlock{D}
GeneralMatrixBlock{D}(m, n, A, tag="matblock(...)")
GeneralMatrixBlock(A; nlevel=2, tag="matblock(...)")
```

一般行列ブロックは、行列演算子を量子ゲートにラップします。これは量子ゲートの最も一般的な形式です。

### 引数

  * `m` と `n` は行と列のディットの数です。
  * `A` は行列です。
  * `tag` は印刷される情報です。
  * `D` と `nlevel` は各クディットのレベルの数です。
