```
geqrf!(A, tau)
```

Calcule la factorisation `QR` de `A`, `A = QR`. `tau` contient des scalaires qui paramètrent les réflecteurs élémentaires de la factorisation. `tau` doit avoir une longueur supérieure ou égale à la plus petite dimension de `A`.

Renvoie `A` et `tau` modifiés sur place.
