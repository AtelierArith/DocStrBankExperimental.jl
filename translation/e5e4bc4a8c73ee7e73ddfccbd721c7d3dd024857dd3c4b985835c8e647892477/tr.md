```
versioninfo(io::IO=stdout; verbose::Bool=false)
```

Kullanımda olan Julia sürümü hakkında bilgi yazdırır. Çıktı, boolean anahtar argümanları ile kontrol edilir:

  * `verbose`: tüm ek bilgileri yazdır

!!! warning
    Bu fonksiyonun çıktısı hassas bilgiler içerebilir. Çıktıyı paylaşmadan önce, lütfen çıktıyı gözden geçirin ve kamuya açık olarak paylaşılmaması gereken verileri kaldırın.


Ayrıca bakınız: [`VERSION`](@ref).
