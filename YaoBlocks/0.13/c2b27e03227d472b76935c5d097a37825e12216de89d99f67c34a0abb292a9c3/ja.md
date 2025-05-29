```
AbstractAdd{D} <: CompositeBlock{D}
```

ハミルトニアン型をサポートすることを目的とした抽象加算インターフェース。

### 必要なインターフェース

  * `chsubblocks`
  * `subblocks`

### 提供するもの

  * `unsafe_apply!` とその逆
  * `mat` とその逆
  * `adjoint`
  * `occupied_locs`
  * `dit` 文字列に対する `getindex`
  * `ishermitian`
