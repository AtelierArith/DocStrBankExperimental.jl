```
ormrq!(taraf, trans, A, tau, C)
```

`Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) için `side = L` veya `side = R` için `gerqf!` kullanılarak hesaplanan `A`'nın `RQ` faktorizasyonundan `Q` kullanarak eşdeğer sağ taraf çarpımı yapar. `C` üzerine yazılır.
