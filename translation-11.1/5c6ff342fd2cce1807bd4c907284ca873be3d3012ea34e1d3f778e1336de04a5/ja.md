```
put!(c::Channel, v)
```

アイテム `v` をチャネル `c` に追加します。チャネルが満杯の場合はブロックします。

バッファなしチャネルの場合、別のタスクによって [`take!`](@ref) が実行されるまでブロックします。

!!! compat "Julia 1.1"
    `v` は、`put!` が呼び出されるときに [`convert`](@ref) を使ってチャネルの型に変換されます。

