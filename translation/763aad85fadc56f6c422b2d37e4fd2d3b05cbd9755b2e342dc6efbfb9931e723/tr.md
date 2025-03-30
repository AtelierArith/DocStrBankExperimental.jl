```
bdsdc!(uplo, compq, d, e_) -> (d, e, u, vt, q, iq)
```

Bidiagonal bir matrisin tekil değer ayrıştırmasını `d` ana köşesinde ve `e_` yan köşesinde böl ve fethet yöntemi kullanarak hesaplar. Eğer `uplo = U` ise, `e_` süperdiagonaldir. Eğer `uplo = L` ise, `e_` alt diagonaldir. Eğer `compq = N` ise, yalnızca tekil değerler bulunur. Eğer `compq = I` ise, tekil değerler ve vektörler bulunur. Eğer `compq = P` ise, tekil değerler ve vektörler kompakt formda bulunur. Sadece gerçek türler için çalışır.

Tekil değerleri `d` içinde döner ve eğer `compq = P` ise, kompakt tekil vektörleri `iq` içinde döner.
