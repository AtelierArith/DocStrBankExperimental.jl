```
gttrs!(trans, dl, d, du, du2, ipiv, B)
```

`A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), veya `adjoint(A) * X = B` (`trans = C`) denklemini `gttrf!` ile hesaplanan `LU` faktorizasyonunu kullanarak çözer. `B`, çözüm `X` ile üzerine yazılır.
