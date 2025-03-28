```
syevr!(jobz, range, uplo, A, vl, vu, il, iu, abstol) -> (W, Z)
```

Trouve les valeurs propres (`jobz = N`) ou les valeurs propres et les vecteurs propres (`jobz = V`) d'une matrice symétrique `A`. Si `uplo = U`, le triangle supérieur de `A` est utilisé. Si `uplo = L`, le triangle inférieur de `A` est utilisé. Si `range = A`, toutes les valeurs propres sont trouvées. Si `range = V`, les valeurs propres dans l'intervalle semi-ouvert `(vl, vu]` sont trouvées. Si `range = I`, les valeurs propres avec des indices entre `il` et `iu` sont trouvées. `abstol` peut être défini comme une tolérance pour la convergence.

Les valeurs propres sont retournées dans `W` et les vecteurs propres dans `Z`.
