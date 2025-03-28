```
gelsd!(A, B, rcond) -> (B, rnk)
```

Calcule la solution de norme minimale de `A * X = B` en trouvant la factorisation `SVD` de `A`, puis en divisant et conquérant le problème. `B` est écrasé avec la solution `X`. Les valeurs singulières inférieures à `rcond` seront considérées comme nulles. Renvoie la solution dans `B` et le rang effectif de `A` dans `rnk`.
