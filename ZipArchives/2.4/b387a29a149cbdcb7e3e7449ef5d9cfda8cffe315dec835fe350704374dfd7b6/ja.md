```
zip_entry_data_offset(r::ZipReader, i::Integer)::Int64
```

エントリ `i` の圧縮データの開始オフセットを、`r` のバッファの開始から返します。

ローカルヘッダーが無効な場合はエラーをスローします。

関連情報として [`zip_compression_method`](@ref) と [`zip_compressed_size`](@ref) を参照してください。
