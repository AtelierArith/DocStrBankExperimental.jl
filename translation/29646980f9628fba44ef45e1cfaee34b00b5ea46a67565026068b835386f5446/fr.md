```
gehrd!(ilo, ihi, A) -> (A, tau)
```

Convertit une matrice `A` en forme de Hessenberg. Si `A` est équilibrée avec `gebal!`, alors `ilo` et `ihi` sont les sorties de `gebal!`. Sinon, ils doivent être `ilo = 1` et `ihi = size(A,2)`. `tau` contient les réflecteurs élémentaires de la factorisation.
