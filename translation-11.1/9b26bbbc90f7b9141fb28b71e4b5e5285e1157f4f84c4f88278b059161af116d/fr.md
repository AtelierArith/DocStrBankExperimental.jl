```
geqrt!(A, nb) -> (A, T)
```

Calcule la factorisation `QR` bloquée de `A`, `A = QR`. `nb` définit la taille du bloc et doit être comprise entre 1 et `n`, la deuxième dimension de `A`.

Renvoie `A`, modifié sur place, et `T`, qui contient des réflecteurs de blocs triangulaires supérieurs qui paramètrent les réflecteurs élémentaires de la factorisation.
