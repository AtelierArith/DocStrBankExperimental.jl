```
gees!(jobvs, A) -> (A, vs, w)
```

Calcule les valeurs propres (`jobvs = N`) ou les valeurs propres et les vecteurs de Schur (`jobvs = V`) de la matrice `A`. `A` est écrasée par sa forme de Schur.

Renvoie `A`, `vs` contenant les vecteurs de Schur, et `w`, contenant les valeurs propres.
