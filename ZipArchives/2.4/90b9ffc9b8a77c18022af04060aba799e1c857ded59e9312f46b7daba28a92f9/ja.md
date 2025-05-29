```
zip_compression_method(x::HasEntries, i::Integer)::UInt16
```

エントリ `i` に使用される圧縮方法を返します。

現在の方法のリストについては、https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT を参照してください。

現在サポートされているのは、Store(0)、Deflate(8)、および Deflate64(9) のみです。

注意: zip ファイルが破損している場合、これは間違っている可能性があります。
