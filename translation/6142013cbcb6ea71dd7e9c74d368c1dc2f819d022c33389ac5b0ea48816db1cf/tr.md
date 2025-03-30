```
bdsqr!(uplo, d, e_, Vt, U, C) -> (d, Vt, U, C)
```

Bidiagonal bir matrisin tekil değer ayrıştırmasını `d` ana köşesinde ve `e_` yan köşesinde hesaplar. Eğer `uplo = U` ise, `e_` üst diyagonaldir. Eğer `uplo = L` ise, `e_` alt diyagonaldir. Ayrıca isteğe bağlı olarak `Q' * C` çarpımını da hesaplayabilir.

Tekil değerleri `d` içinde döner ve matris `C`, `Q' * C` ile üzerine yazılır.
