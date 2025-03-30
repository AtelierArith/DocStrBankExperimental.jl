```
rot!(n, X, incx, Y, incy, c, s)
```

`X`'i `c*X + s*Y` ile ve `Y`'yi `-conj(s)*X + c*Y` ile ilk `n` elemanı `incx` adım aralığına sahip dizi `X` için ve ilk `n` elemanı `incy` adım aralığına sahip dizi `Y` için üst üste yazar. `X` ve `Y`'yi döner.

!!! uyumluluk "Julia 1.5"
    `rot!` en az Julia 1.5 gerektirir.

