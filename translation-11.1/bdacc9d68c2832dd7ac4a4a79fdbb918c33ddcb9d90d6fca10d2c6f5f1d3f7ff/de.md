```
gelsd!(A, B, rcond) -> (B, rnk)
```

Berechnet die Lösung mit der kleinsten Norm von `A * X = B`, indem die `SVD`-Faktorisierung von `A` gefunden wird, und dann das Problem durch Teilen und Erobern gelöst wird. `B` wird mit der Lösung `X` überschrieben. Singuläre Werte unter `rcond` werden als null behandelt. Gibt die Lösung in `B` und den effektiven Rang von `A` in `rnk` zurück.
