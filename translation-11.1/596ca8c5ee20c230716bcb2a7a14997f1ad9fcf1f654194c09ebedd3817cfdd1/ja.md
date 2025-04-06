```
readbytes!(stream::IO, b::AbstractVector{UInt8}, nb=length(b))
```

ストリームから最大 `nb` バイトを `b` に読み込み、読み込まれたバイト数を返します。必要に応じて `b` のサイズは増加します（つまり、`nb` が `length(b)` より大きく、十分なバイトが読み込まれた場合）、ただし減少することはありません。
