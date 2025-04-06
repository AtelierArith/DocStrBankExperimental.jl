```
pstrf!(uplo, A, tol) -> (A, piv, rank, info)
```

Pozitif tanımlı matris `A`'nın kullanıcı tarafından belirlenen tolerans `tol` ile pivotlu Cholesky ayrıştırmasını (eğer `uplo = U` ise üst, `uplo = L` ise alt) hesaplar. `A`, Cholesky ayrıştırması ile üzerine yazılır.

`A`, pivotlar `piv`, `A`'nın rengi ve bir `info` kodu döner. Eğer `info = 0` ise, ayrıştırma başarılı olmuştur. Eğer `info = i > 0` ise, o zaman `A` belirsiz veya rengi eksiktir.
