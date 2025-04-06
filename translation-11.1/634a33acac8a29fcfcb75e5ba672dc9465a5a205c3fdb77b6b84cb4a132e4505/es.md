```
sygvd!(itype, jobz, uplo, A, B) -> (w, A, B)
```

Encuentra los valores propios generalizados (`jobz = N`) o valores propios y vectores propios (`jobz = V`) de una matriz simétrica `A` y una matriz simétrica definida positiva `B`. Si `uplo = U`, se utilizan los triángulos superiores de `A` y `B`. Si `uplo = L`, se utilizan los triángulos inferiores de `A` y `B`. Si `itype = 1`, el problema a resolver es `A * x = lambda * B * x`. Si `itype = 2`, el problema a resolver es `A * B * x = lambda * x`. Si `itype = 3`, el problema a resolver es `B * A * x = lambda * x`.
