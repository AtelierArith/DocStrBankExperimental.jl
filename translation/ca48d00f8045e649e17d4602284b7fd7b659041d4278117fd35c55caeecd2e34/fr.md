```
geqrt3!(A) -> (A, T)
```

Calcule de manière récursive la factorisation `QR` bloquée de `A`, `A = QR`.

Renvoie `A`, modifié sur place, et `T`, qui contient des réflecteurs de blocs triangulaires supérieurs qui paramètrent les réflecteurs élémentaires de la factorisation.
