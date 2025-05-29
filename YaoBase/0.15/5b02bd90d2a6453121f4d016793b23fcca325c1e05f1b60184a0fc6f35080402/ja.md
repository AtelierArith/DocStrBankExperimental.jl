```
general_controlled_gates(num_bit::Int, projectors::Vector{Tp}, cbits::Vector{Int}, gates::Vector{AbstractMatrix}, locs::Vector{Int}) -> AbstractMatrix
```

`num_bit` 個のクディットのヒルベルト空間における一般的な多重制御ゲートを返します。

  * `projectors` は、特定の位置での逆制御と制御のためにしばしば `P0` と `P1` として選択されます。
  * `cbits` は `projectors` と同じ長さである必要があり、制御位置を指定します。
  * `gates` は制御された単一量子ビットゲートのリストです。
  * `locs` は `gates` と同じ長さである必要があり、ゲートの位置を指定します。
