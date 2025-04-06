```
geqrt3!(A, T)
```

Calcule récursivement la factorisation `QR` bloquée de `A`, `A = QR`. `T` contient des réflecteurs de blocs triangulaires supérieurs qui paramètrent les réflecteurs élémentaires de la factorisation. La première dimension de `T` définit la taille du bloc et doit être comprise entre 1 et `n`. La deuxième dimension de `T` doit être égale à la plus petite dimension de `A`.

Renvoie `A` et `T` modifiés sur place.
