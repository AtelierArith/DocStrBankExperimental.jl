```
zip_stored_crc32(x::HasEntries, i::Integer)::UInt32
```

中央ディレクトリのエントリ `i` のマークされた crc32 を返します。

注意: zip ファイルが破損している場合、これは間違っている可能性があります。

参照: [`zip_crc32`](@ref), [`zip_test_entry`](@ref).
