```
sytri!(uplo, A, ipiv)
```

Simetrik bir matris `A`'nın tersini `sytrf!` sonuçlarını kullanarak hesaplar. Eğer `uplo = U` ise, `A`'nın üst yarısı saklanır. Eğer `uplo = L` ise, alt yarısı saklanır. `A`, tersine yazılır.
