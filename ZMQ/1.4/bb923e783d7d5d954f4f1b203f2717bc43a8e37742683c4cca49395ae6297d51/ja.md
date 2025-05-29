```
send(socket::Socket, data; more=false)
```

`data`を`socket`経由で送信します。`more=true`キーワード引数を渡すことで、`data`がより大きなマルチパートメッセージの一部であることを示すことができます。`data`は任意の`isbits`型、`isbits`要素の`Vector`、`String`、または大きな配列のゼロコピー送信を行うための[`Message`](@ref)オブジェクトであることができます。
