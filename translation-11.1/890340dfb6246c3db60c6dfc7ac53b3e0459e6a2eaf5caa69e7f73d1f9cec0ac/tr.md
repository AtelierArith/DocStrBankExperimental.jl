```
gemqrt!(taraf, trans, V, T, C)
```

`Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) için `side = L` veya `side = R` için `geqrt!` kullanılarak hesaplanan `A`'nın `QR` faktorizasyonundan `Q` kullanarak eşdeğer sağ taraf çarpımı yapar. `C` üzerine yazılır.
