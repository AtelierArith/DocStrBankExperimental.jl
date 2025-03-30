```
open(command, stdio=devnull; write::Bool = false, read::Bool = !write)
```

`command`'ı asenkron olarak çalıştırmaya başlayın ve bir `process::IO` nesnesi döndürün. Eğer `read` doğruysa, o zaman süreçten okunan veriler sürecin standart çıktısından gelir ve `stdio` isteğe bağlı olarak sürecin standart giriş akışını belirtir. Eğer `write` doğruysa, o zaman yazmalar sürecin standart girişine gider ve `stdio` isteğe bağlı olarak sürecin standart çıkış akışını belirtir. Sürecin standart hata akışı mevcut küresel `stderr` ile bağlantılıdır.
