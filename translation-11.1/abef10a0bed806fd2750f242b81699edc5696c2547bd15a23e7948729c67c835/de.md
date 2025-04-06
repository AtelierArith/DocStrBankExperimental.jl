```
ormrz!(seite, trans, A, tau, C)
```

Multipliziert die Matrix `C` mit `Q` aus der durch `tzrzf!` gelieferten Transformation. Je nach `seite` oder `trans` kann die Multiplikation linksseitig (`seite = L, Q*C`) oder rechtsseitig (`seite = R, C*Q`) sein, und `Q` kann unverändert (`trans = N`), transponiert (`trans = T`) oder konjugiert transponiert (`trans = C`) sein. Gibt die Matrix `C` zurück, die in-place mit dem Ergebnis der Multiplikation modifiziert wird.
