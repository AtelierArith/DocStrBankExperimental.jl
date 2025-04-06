```
GC.enable(on::Bool)
```

Contrôlez si la collecte des ordures est activée en utilisant un argument booléen (`true` pour activé, `false` pour désactivé). Retournez l'état précédent de la collecte des ordures.

!!! warning
    Désactiver la collecte des ordures ne doit être utilisé qu'avec prudence, car cela peut entraîner une augmentation illimitée de l'utilisation de la mémoire.

