```
posv!(uplo, A, B) -> (A, B)
```

`A` simetrik veya Hermitian pozitif belirli bir matris olduğunda `A * X = B` denkleminin çözümünü bulur. Eğer `uplo = U` ise `A`'nın üst Cholesky ayrıştırması hesaplanır. Eğer `uplo = L` ise `A`'nın alt Cholesky ayrıştırması hesaplanır. `A`, Cholesky ayrıştırması ile üzerine yazılır. `B`, çözüm `X` ile üzerine yazılır.
