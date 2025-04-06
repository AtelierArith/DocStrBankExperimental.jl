```
trtrs!(uplo, trans, diag, A, B)
```

`A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), veya `adjoint(A) * X = B` (`trans = C`) için (üstse `uplo = U`, altse `uplo = L`) üçgen matris `A`'yı çözer. Eğer `diag = N` ise, `A`'nın birim olmayan diyagonal elemanları vardır. Eğer `diag = U` ise, `A`'nın tüm diyagonal elemanları birdir. `B`, çözüm `X` ile üzerine yazılır.
