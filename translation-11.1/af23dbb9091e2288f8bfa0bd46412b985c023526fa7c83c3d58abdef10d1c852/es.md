```
ormqr!(lado, trans, A, tau, C)
```

Calcula `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) para `lado = L` o la multiplicación equivalente por la derecha para `lado = R` utilizando `Q` de una factorización `QR` de `A` calculada usando `geqrf!`. `C` es sobrescrito.
