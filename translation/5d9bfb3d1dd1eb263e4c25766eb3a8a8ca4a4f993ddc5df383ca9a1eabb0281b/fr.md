```
stegr!(jobz, range, dv, ev, vl, vu, il, iu) -> (w, Z)
```

Calcule les valeurs propres (`jobz = N`) ou les valeurs propres et les vecteurs propres (`jobz = V`) pour une matrice tridiagonale symétrique avec `dv` comme diagonale et `ev` comme hors-diagonale. Si `range = A`, toutes les valeurs propres sont trouvées. Si `range = V`, les valeurs propres dans l'intervalle semi-ouvert `(vl, vu]` sont trouvées. Si `range = I`, les valeurs propres avec des indices entre `il` et `iu` sont trouvées. Les valeurs propres sont retournées dans `w` et les vecteurs propres dans `Z`.
