```
mktemp(parent=tempdir(); cleanup=true) -> (path, io)
```

`(path, io)` döndür, burada `path` yeni bir geçici dosyanın `parent` içindeki yolu ve `io` bu yol için açık bir dosya nesnesidir. `cleanup` seçeneği, geçici dosyanın işlem sona erdiğinde otomatik olarak silinip silinmeyeceğini kontrol eder.

!!! compat "Julia 1.3"
    `cleanup` anahtar argümanı Julia 1.3'te eklendi. İlgili olarak, 1.3'ten itibaren, Julia, `cleanup` açıkça `false` olarak ayarlanmamışsa, Julia işlemi sona erdiğinde `mktemp` ile oluşturulan geçici yolları silecektir.

