```
stringmime(mime, x; context=nothing)
```

指定された `mime` タイプでの `x` の表現を含む `AbstractString` を返します。これは [`repr(mime, x)`](@ref) に似ていますが、バイナリデータは ASCII 文字列として base64 エンコードされます。

オプションのキーワード引数 `context` は `:key=>value` ペア、または [`show`](@ref) に渡される I/O ストリームに使用される属性を持つ `IO` または [`IOContext`](@ref) オブジェクトに設定できます。
