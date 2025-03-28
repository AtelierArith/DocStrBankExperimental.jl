```
orgql!(A, tau, k = length(tau))
```

Trouve explicitement la matrice `Q` d'une factorisation `QL` après avoir appelé `geqlf!` sur `A`. Utilise la sortie de `geqlf!`. `A` est écrasé par `Q`.
