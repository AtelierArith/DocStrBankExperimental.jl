```
scal!(n, a, X, incx)
scal!(a, X)
```

Dizinin ilk `n` elemanını `incx` adımıyla `a*X` ile değiştirmek için `X`'i üzerine yazar. `X`'i döndürür.

Eğer `n` ve `incx` sağlanmamışsa, `length(X)` ve `stride(X,1)` kullanılır.
