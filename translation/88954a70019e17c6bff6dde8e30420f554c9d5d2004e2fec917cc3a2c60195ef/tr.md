```
sysv!(uplo, A, B) -> (B, A, ipiv)
```

`A * X = B` eşitliğini simetrik matris `A` için çözer. Eğer `uplo = U` ise, `A`'nın üst yarısı saklanır. Eğer `uplo = L` ise, alt yarısı saklanır. `B`, çözüm `X` ile üzerine yazılır. `A`, Bunch-Kaufman faktorizasyonu ile üzerine yazılır. `ipiv`, faktorizasyon hakkında pivotlama bilgilerini içerir.
