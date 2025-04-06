```
hesv!(uplo, A, B) -> (B, A, ipiv)
```

Hermit matris `A` için `A * X = B` çözümünü bulur. Eğer `uplo = U` ise, `A`'nın üst yarısı saklanır. Eğer `uplo = L` ise, alt yarısı saklanır. `B`, çözüm `X` ile üzerine yazılır. `A`, Bunch-Kaufman faktörizasyonu ile üzerine yazılır. `ipiv`, faktörizasyon hakkında pivot bilgilerini içerir.
