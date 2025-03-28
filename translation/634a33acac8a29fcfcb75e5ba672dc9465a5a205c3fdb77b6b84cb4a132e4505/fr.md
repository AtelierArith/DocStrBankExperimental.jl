```
sygvd!(itype, jobz, uplo, A, B) -> (w, A, B)
```

Trouve les valeurs propres généralisées (`jobz = N`) ou les valeurs propres et vecteurs propres (`jobz = V`) d'une matrice symétrique `A` et d'une matrice symétrique définie positive `B`. Si `uplo = U`, les triangles supérieurs de `A` et `B` sont utilisés. Si `uplo = L`, les triangles inférieurs de `A` et `B` sont utilisés. Si `itype = 1`, le problème à résoudre est `A * x = lambda * B * x`. Si `itype = 2`, le problème à résoudre est `A * B * x = lambda * x`. Si `itype = 3`, le problème à résoudre est `B * A * x = lambda * x`.
