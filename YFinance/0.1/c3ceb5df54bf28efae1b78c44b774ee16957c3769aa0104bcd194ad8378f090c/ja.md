```
validate_symbol(symbol::AbstractString)
```

シンボル（ティッカー）を検証します。ティッカーが有効な場合は `true` を返し、無効な場合は `false` を返します。

# 引数

  * `symbol::String` はティッカーです（例：Apple Computers の AAPL、または S&P500 の ^GSPC）

# 仕組み

HTTP リクエストが機能するか（ステータス 200）を確認するか、リクエストがエラーになるか（この場合の一般的なステータス：404）を確認します。
