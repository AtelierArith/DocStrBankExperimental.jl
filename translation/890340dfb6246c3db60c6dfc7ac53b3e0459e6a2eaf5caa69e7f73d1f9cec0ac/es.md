```
gemqrt!(lado, trans, V, T, C)
```

Calcula `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) para `lado = L` o la multiplicación equivalente del lado derecho para `lado = R` utilizando `Q` de una factorización `QR` de `A` calculada usando `geqrt!`. `C` es sobrescrito.
