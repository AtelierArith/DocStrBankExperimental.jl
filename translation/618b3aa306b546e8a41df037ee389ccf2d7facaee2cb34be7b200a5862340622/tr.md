```
gels!(trans, A, B) -> (F, B, ssr)
```

`A * X = B`, `transpose(A) * X = B` veya `adjoint(A) * X = B` lineer denklemini QR veya LQ faktorizasyonu kullanarak çözer. Çözümü içindeki `B` matrisini/vektörünü yerinde değiştirir. `A`, `QR` veya `LQ` faktorizasyonu ile üzerine yazılır. `trans`, `N` (değişiklik yok), `T` (transpose) veya `C` (konjugat transpose) olabilir. `gels!`, minimum norm/en küçük kareler çözümünü arar. `A` alt veya üst belirlenmiş olabilir. Çözüm `B` içinde döndürülür.
