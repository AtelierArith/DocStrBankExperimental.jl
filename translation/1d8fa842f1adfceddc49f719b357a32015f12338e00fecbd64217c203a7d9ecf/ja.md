```
Profile.Allocs.print([io::IO = stdout,] [data::AllocResults = fetch()]; kwargs...)
```

`io` にプロファイリング結果を出力します（デフォルトは `stdout`）。`data` ベクターを提供しない場合、蓄積されたバックトレースの内部バッファが使用されます。

有効なキーワード引数の説明については `Profile.print` を参照してください。
