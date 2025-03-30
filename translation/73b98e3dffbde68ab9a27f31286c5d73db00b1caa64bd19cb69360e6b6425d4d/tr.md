```
geqp3!(A, [jpvt, tau]) -> (A, tau, jpvt)
```

`A` matrisinin pivotlu `QR` faktorizasyonunu `AP = QR` hesaplayın, BLAS seviye 3 kullanarak. `P`, `jpvt` ile temsil edilen bir pivotlama matrisidir. `tau`, temel yansıtıcıları saklar. `jpvt` ve `tau` argümanları isteğe bağlıdır ve önceden tahsis edilmiş dizilerin geçirilmesine izin verir. Geçirildiğinde, `jpvt`'nin uzunluğu `A` bir `(m x n)` matrisiyse `n`'den büyük veya eşit olmalıdır ve `tau`'nun uzunluğu `A`'nın en küçük boyutundan büyük veya eşit olmalıdır. Girişte, eğer `jpvt[j]` sıfıra eşit değilse, `A`'nın `j`'inci sütunu `AP`'nin önüne permütasyon edilir.

`A`, `jpvt` ve `tau` yerinde değiştirilir.
