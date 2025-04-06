```
getrf!(A) -> (A, ipiv, info)
```

`A`'nın pivotlu `LU` faktorizasyonunu hesaplayın, `A = LU`.

`A`'yı yerinde değiştirilmiş olarak, `ipiv`'yi, pivotlama bilgisini ve başarıyı belirten bir `info` kodunu döndürür (`info = 0`), `U`'da bir tekil değer (`info = i`, bu durumda `U[i,i]` tekildir) veya bir hata kodu (`info < 0`).
