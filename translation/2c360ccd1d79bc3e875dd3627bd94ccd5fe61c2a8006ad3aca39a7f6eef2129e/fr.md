```
gges!(jobvsl, jobvsr, A, B) -> (A, B, alpha, beta, vsl, vsr)
```

Calcule les valeurs propres généralisées, la forme de Schur généralisée, les vecteurs de Schur à gauche (`jobsvl = V`), ou les vecteurs de Schur à droite (`jobvsr = V`) de `A` et `B`.

Les valeurs propres généralisées sont retournées dans `alpha` et `beta`. Les vecteurs de Schur à gauche sont retournés dans `vsl` et les vecteurs de Schur à droite sont retournés dans `vsr`.
