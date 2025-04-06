```
ormrq!(lado, trans, A, tau, C)
```

Calcula `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) para `lado = L` o la multiplicación equivalente por la derecha para `lado = R` usando `Q` de una factorización `RQ` de `A` calculada usando `gerqf!`. `C` es sobrescrito.
