```
trtri!(uplo, diag, A)
```

Üst (eğer `uplo = U`) veya alt (eğer `uplo = L`) üçgen matris `A`nın tersini bulur. Eğer `diag = N` ise, `A`nın birim olmayan köşegen elemanları vardır. Eğer `diag = U` ise, `A`nın tüm köşegen elemanları birdir. `A`, tersine yazılır.
