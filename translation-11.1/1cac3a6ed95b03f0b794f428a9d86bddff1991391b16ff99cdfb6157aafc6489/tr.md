```
download(url::AbstractString, [path::AbstractString = tempname()]) -> path
```

Verilen url'den bir dosya indirir, dosyayı `path` konumuna kaydeder veya belirtilmemişse geçici bir konuma kaydeder. İndirilen dosyanın yolunu döner.

!!! note
    Julia 1.6'dan itibaren, bu fonksiyon kullanımdan kaldırılmıştır ve sadece `Downloads.download` etrafında ince bir sarmalayıcıdır. Yeni kodda, bu fonksiyonu doğrudan çağırmak yerine kullanmalısınız.

