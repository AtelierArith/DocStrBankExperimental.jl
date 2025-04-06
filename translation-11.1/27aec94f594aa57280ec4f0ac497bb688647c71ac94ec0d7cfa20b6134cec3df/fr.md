```
syev!(jobz, uplo, A)
```

Trouve les valeurs propres (`jobz = N`) ou les valeurs propres et les vecteurs propres (`jobz = V`) d'une matrice symétrique `A`. Si `uplo = U`, le triangle supérieur de `A` est utilisé. Si `uplo = L`, le triangle inférieur de `A` est utilisé.
