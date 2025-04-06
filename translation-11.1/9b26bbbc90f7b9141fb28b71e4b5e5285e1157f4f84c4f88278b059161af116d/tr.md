```
geqrt!(A, nb) -> (A, T)
```

`A`'n bloklu `QR` faktorizasyonunu hesaplar, `A = QR`. `nb` blok boyutunu ayarlar ve 1 ile `A`'nın ikinci boyutu `n` arasında olmalıdır.

Yerinde değiştirilen `A`'yı ve faktorizasyonun temel yansıtıcılarını parametreleyen üst üçgen blok yansıtıcılarını içeren `T`'yi döndürür.
