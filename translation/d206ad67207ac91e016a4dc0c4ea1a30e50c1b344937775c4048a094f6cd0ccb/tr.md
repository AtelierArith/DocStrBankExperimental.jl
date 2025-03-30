```
getrf!(A, ipiv) -> (A, ipiv, info)
```

`A`'nın pivotlu `LU` faktorizasyonunu hesaplayın, `A = LU`. `ipiv` pivotlama bilgilerini içerir ve `info` başarıyı (`info = 0`), `U`'da bir tekil değeri (`info = i`, bu durumda `U[i,i]` tekildir) veya bir hata kodunu (`info < 0`) gösteren bir kod içerir.
