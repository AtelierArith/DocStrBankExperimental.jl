```
stev!(job, dv, ev) -> (dv, Zmat)
```

Calcule le système d'autovalues pour une matrice tridiagonale symétrique avec `dv` comme diagonale et `ev` comme hors-diagonale. Si `job = N`, seuls les autovalues sont trouvés et retournés dans `dv`. Si `job = V`, alors les vecteurs propres sont également trouvés et retournés dans `Zmat`.
