```
gbtrs!(trans, kl, ku, m, AB, ipiv, B)
```

方程式 `AB * X = B` を解きます。`trans` は `AB` の向きを決定します。`N`（転置なし）、`T`（転置）、または `C`（共役転置）のいずれかです。`kl` は非ゼロバンドを含む最初の下対角線、`ku` はそれを含む最後の上対角線、`m` は行列 `AB` の最初の次元です。`ipiv` は `gbtrf!` から返されるピボットのベクトルです。ベクトルまたは行列 `X` を返し、`B` をその場で上書きします。
