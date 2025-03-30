```
clear!(syms, pids=workers(); mod=Main)
```

Modüllerdeki global bağlamaları `nothing` ile başlatarak temizler. `syms` [`Symbol`](@ref) türünde veya `Symbol` koleksiyonu olmalıdır. `pids` ve `mod`, global değişkenlerin yeniden başlatılacağı süreçleri ve modülü tanımlar. Sadece `mod` altında tanımlı olan isimler temizlenir.

Bir global sabitin temizlenmesi istendiğinde bir istisna oluşur.
