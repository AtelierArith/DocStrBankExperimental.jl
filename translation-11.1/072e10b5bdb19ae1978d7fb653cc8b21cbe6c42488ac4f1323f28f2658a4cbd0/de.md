```
orglq!(A, tau, k = length(tau))
```

Findet explizit die Matrix `Q` einer `LQ`-Faktorisierung nach dem Aufruf von `gelqf!` auf `A`. Verwendet die Ausgabe von `gelqf!`. `A` wird durch `Q` überschrieben.
