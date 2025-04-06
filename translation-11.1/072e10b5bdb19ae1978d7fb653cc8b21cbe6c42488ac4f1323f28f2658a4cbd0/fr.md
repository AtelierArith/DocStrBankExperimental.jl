```
orglq!(A, tau, k = length(tau))
```

Trouve explicitement la matrice `Q` d'une factorisation `LQ` après avoir appelé `gelqf!` sur `A`. Utilise la sortie de `gelqf!`. `A` est écrasé par `Q`.
