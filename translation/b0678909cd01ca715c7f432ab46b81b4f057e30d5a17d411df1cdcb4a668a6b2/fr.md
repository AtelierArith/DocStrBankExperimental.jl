```
gecon!(normtype, A, anorm)
```

Trouve le nombre de condition réciproque de la matrice `A`. Si `normtype = I`, le nombre de condition est trouvé dans la norme infinie. Si `normtype = O` ou `1`, le nombre de condition est trouvé dans la norme un. `A` doit être le résultat de `getrf!` et `anorm` est la norme de `A` dans la norme pertinente.
