```
gemqrt!(côté, trans, V, T, C)
```

Calcule `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) pour `côté = L` ou la multiplication équivalente à droite pour `côté = R` en utilisant `Q` d'une factorisation `QR` de `A` calculée à l'aide de `geqrt!`. `C` est écrasé.
