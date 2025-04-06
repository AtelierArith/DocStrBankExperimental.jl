```
gelsy!(A, B, rcond) -> (B, rnk)
```

Calcule la solution de norme minimale de `A * X = B` en trouvant la factorisation complète `QR` de `A`, puis en divisant et conquérant le problème. `B` est écrasé avec la solution `X`. Les valeurs singulières inférieures à `rcond` seront traitées comme zéro. Renvoie la solution dans `B` et le rang effectif de `A` dans `rnk`.
