```
ggev!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

Trouve la décomposition des valeurs propres généralisées de `A` et `B`. Si `jobvl = N`, les vecteurs propres à gauche ne sont pas calculés. Si `jobvr = N`, les vecteurs propres à droite ne sont pas calculés. Si `jobvl = V` ou `jobvr = V`, les vecteurs propres correspondants sont calculés.
