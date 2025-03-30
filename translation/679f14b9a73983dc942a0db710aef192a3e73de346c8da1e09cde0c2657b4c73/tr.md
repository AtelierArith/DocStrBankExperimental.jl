```
sytrs!(uplo, A, ipiv, B)
```

Simetrik matris `A` için `A * X = B` denklemini `sytrf!` sonuçlarını kullanarak çözer. Eğer `uplo = U` ise, `A`'nın üst yarısı saklanır. Eğer `uplo = L` ise, alt yarısı saklanır. `B`, çözüm `X` ile üzerine yazılır.
