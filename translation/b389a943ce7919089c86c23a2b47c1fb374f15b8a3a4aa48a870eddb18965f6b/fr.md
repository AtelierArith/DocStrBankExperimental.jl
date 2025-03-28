```
ormql!(side, trans, A, tau, C)
```

Calcule `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) pour `side = L` ou la multiplication équivalente à droite pour `side = R` en utilisant `Q` d'une factorisation `QL` de `A` calculée à l'aide de `geqlf!`. `C` est écrasé.
