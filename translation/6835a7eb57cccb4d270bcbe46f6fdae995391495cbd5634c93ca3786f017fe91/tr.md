```
link_pipe!(pipe; reader_supports_async=false, writer_supports_async=false)
```

`pipe`'i başlatın ve `in` uç noktasını `out` uç noktasına bağlayın. Anahtar kelime argümanları `reader_supports_async`/`writer_supports_async`, Windows'ta `OVERLAPPED` ve POSIX sistemlerinde `O_NONBLOCK` ile ilişkilidir. Harici bir program tarafından kullanılmayacaklarsa (örneğin, [`run`](@ref) ile yürütülen bir komutun çıktısı gibi) `true` olmalıdırlar.
