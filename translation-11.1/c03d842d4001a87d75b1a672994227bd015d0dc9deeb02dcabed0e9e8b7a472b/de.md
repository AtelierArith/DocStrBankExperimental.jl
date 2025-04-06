```
orgrq!(A, tau, k = length(tau))
```

Findet explizit die Matrix `Q` einer `RQ`-Faktorisierung, nachdem `gerqf!` auf `A` aufgerufen wurde. Verwendet die Ausgabe von `gerqf!`. `A` wird durch `Q` überschrieben.
