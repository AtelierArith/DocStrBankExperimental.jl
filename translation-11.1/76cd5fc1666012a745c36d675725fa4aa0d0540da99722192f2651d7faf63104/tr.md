```
trcon!(norm, uplo, diag, A)
```

`A` (eğer `uplo = U` ise üst, `uplo = L` ise alt) üçgen matrisinin ters koşul sayısını bulur. Eğer `diag = N` ise, `A` birim olmayan diyagonal elemanlara sahiptir. Eğer `diag = U` ise, `A`'nın tüm diyagonal elemanları birdir. Eğer `norm = I` ise, koşul sayısı sonsuz normda bulunur. Eğer `norm = O` veya `1` ise, koşul sayısı bir normda bulunur.
