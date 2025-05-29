```
hilbertkron(num_bit::Int, gates::Vector{AbstractMatrix}, locs::Vector{Int}; nlevel=2) -> AbstractMatrix
```

`num_bit` 個のクディットのヒルベルト空間におけるゲートの一般的なクロネッカー積形式を返します。

  * `gates` は行列のリストです。
  * `start_locs` は `gates` と同じ長さである必要があり、ゲートの開始位置を指定します。
