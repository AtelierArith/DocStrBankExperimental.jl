```
savecube(cube,name::String)
```

[`YAXArray`](@ref)を`path`に保存します。

# 拡張ヘルプ

キーワード引数は次のとおりです：

  * `name`:
  * `datasetaxis="Variable"` カテゴリカル軸の特別な処理で、別々のzarr配列に書き込まれます
  * `max_cache`: データ処理のために使用されるビット数。
  * `backend`: データを保存するために使用されるバックエンド。パスの拡張子に従ってバックエンドを検索します。
  * `driver`: `backend`と同じ設定。
  * `overwrite::Bool=false` 既に存在する場合はキューブを上書きします。
