```
geqrt!(A, T)
```

`A`'nın bloklu `QR` faktorizasyonunu hesaplar, `A = QR`. `T`, faktorizasyonun temel yansıtıcılarını parametreleyen üst üçgen blok yansıtıcılarını içerir. `T`'nin ilk boyutu blok boyutunu belirler ve 1 ile `n` arasında olmalıdır. `T`'nin ikinci boyutu `A`'nın en küçük boyutuna eşit olmalıdır.

Yerinde değiştirilmiş `A` ve `T` döner.
