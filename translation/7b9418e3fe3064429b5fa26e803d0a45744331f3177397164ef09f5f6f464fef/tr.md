```
iterate(iter [, state]) -> Union{Nothing, Tuple{Any, Any}}
```

İteratörü bir sonraki öğeyi elde etmek için ilerletin. Eğer hiçbir öğe kalmadıysa, `nothing` döndürülmelidir. Aksi takdirde, bir sonraki öğe ve yeni iterasyon durumu içeren 2-tuple döndürülmelidir.
