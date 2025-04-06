```
unwatch_folder(path::AbstractString)
```

Arrêtez le suivi en arrière-plan des modifications pour `path`. Il n'est pas recommandé de faire cela pendant qu'une autre tâche attend que `watch_folder` retourne sur le même chemin, car le résultat peut être imprévisible.
