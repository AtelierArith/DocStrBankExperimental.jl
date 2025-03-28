```
ormlq!(côté, trans, A, tau, C)
```

Calcule `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) pour `côté = L` ou la multiplication équivalente à droite pour `côté = R` en utilisant `Q` d'une factorisation `LQ` de `A` calculée à l'aide de `gelqf!`. `C` est écrasé.
