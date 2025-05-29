```
zip_compressed_size(x::HasEntries, i::Integer)::UInt64
```

エントリ `i` のマークされた圧縮サイズをバイト数で返します。

注意: zipファイルが破損している場合、これは間違っている可能性があります。
