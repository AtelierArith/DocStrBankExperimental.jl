```
gesv!(A, B) -> (B, A, ipiv)
```

`A * X = B` doğrusal denklemini çözer; burada `A` kare bir matristir ve `A`'nın `LU` faktorizasyonu kullanılır. `A`, `LU` faktorizasyonu ile üzerine yazılır ve `B`, çözüm `X` ile üzerine yazılır. `ipiv`, `A`'nın `LU` faktorizasyonu için pivotlama bilgilerini içerir.
