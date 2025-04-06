```
open_exclusive(path::String; mode, poll_interval, wait, stale_age, refresh) :: File
```

Okuma yazma tavsiye edici özel erişim için yeni bir dosya oluşturur. Eğer `wait` `false` ise, kilit dosyaları mevcutsa hata verir, aksi takdirde kilidi alana kadar engeller.

Anahtar argümanların açıklaması için [`mkpidlock`](@ref) kısmına bakın.
