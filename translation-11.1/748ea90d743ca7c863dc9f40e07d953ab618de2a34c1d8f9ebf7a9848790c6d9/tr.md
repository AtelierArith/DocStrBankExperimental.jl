```
trexc!(compq, ifst, ilst, T, Q) -> (T, Q)
trexc!(ifst, ilst, T, Q) -> (T, Q)
```

Bir matrisin Schur faktörizasyonu `T`'sini yeniden düzenleyin, böylece `T`'nin `ifst` satır indeksi ile olan diyagonal bloğu `ilst` satır indeksine taşınır. Eğer `compq = V` ise, Schur vektörleri `Q` yeniden düzenlenir. Eğer `compq = N` ise, değiştirilmezler. 4-arg yöntemi, `compq = V` ile 5-arg yöntemini çağırır.
