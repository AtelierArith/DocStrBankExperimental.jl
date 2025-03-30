```
ormql!(side, trans, A, tau, C)
```

`Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) için `side = L` veya `side = R` için `A`'nın `geqlf!` kullanılarak hesaplanan `QL` faktorizasyonundan `Q` kullanarak eşdeğer sağ taraf çarpımı hesaplar. `C` üzerine yazılır.
