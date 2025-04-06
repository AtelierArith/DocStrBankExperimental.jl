```
trevc!(side, howmny, select, T, VL = similar(T), VR = similar(T))
```

Trouve le système d'eigen de la matrice triangulaire supérieure `T`. Si `side = R`, les vecteurs propres droits sont calculés. Si `side = L`, les vecteurs propres gauches sont calculés. Si `side = B`, les deux ensembles sont calculés. Si `howmny = A`, tous les vecteurs propres sont trouvés. Si `howmny = B`, tous les vecteurs propres sont trouvés et rétrotransformés en utilisant `VL` et `VR`. Si `howmny = S`, seuls les vecteurs propres correspondant aux valeurs dans `select` sont calculés.
