```
stebz!(range, order, vl, vu, il, iu, abstol, dv, ev) -> (dv, iblock, isplit)
```

Calcule les valeurs propres pour une matrice tridiagonale symétrique avec `dv` comme diagonale et `ev` comme hors-diagonale. Si `range = A`, toutes les valeurs propres sont trouvées. Si `range = V`, les valeurs propres dans l'intervalle semi-ouvert `(vl, vu]` sont trouvées. Si `range = I`, les valeurs propres avec des indices entre `il` et `iu` sont trouvées. Si `order = B`, les valeurs propres sont ordonnées dans un bloc. Si `order = E`, elles sont ordonnées à travers tous les blocs. `abstol` peut être défini comme une tolérance pour la convergence.
