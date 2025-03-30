```
trrfs!(uplo, trans, diag, A, B, X, Ferr, Berr) -> (Ferr, Berr)
```

`A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), `adjoint(A) * X = B` (`trans = C`) için çözümdeki hatayı tahmin eder; `side = L` için veya `trtrs!` kullanarak `X`'i hesapladıktan sonra sağa doğru `side = R` `X * A` için eşdeğer denklemler. Eğer `uplo = U` ise, `A` üst üçgenlidir. Eğer `uplo = L` ise, `A` alt üçgenlidir. Eğer `diag = N` ise, `A` birim olmayan diyagonal elemanlara sahiptir. Eğer `diag = U` ise, `A`'nın tüm diyagonal elemanları birdir. `Ferr` ve `Berr` isteğe bağlı girdilerdir. `Ferr` ileri hata ve `Berr` geri hatadır, her biri bileşen bazında.
