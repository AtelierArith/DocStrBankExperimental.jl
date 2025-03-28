```
ormql!(lado, trans, A, tau, C)
```

Calcula `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) para `lado = L` o la multiplicación equivalente del lado derecho para `lado = R` usando `Q` de una factorización `QL` de `A` calculada usando `geqlf!`. `C` es sobrescrito.
