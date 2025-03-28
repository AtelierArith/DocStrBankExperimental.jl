```
@async
```

Enveloppez une expression dans une [`Task`](@ref) et ajoutez-la à la file d'attente du planificateur de la machine locale.

Les valeurs peuvent être interpolées dans `@async` via `$`, ce qui copie la valeur directement dans la fermeture sous-jacente construite. Cela vous permet d'insérer la *valeur* d'une variable, isolant le code asynchrone des changements de la valeur de la variable dans la tâche actuelle.

!!! warning
    Il est fortement recommandé de privilégier `Threads.@spawn` plutôt que `@async` toujours **même lorsque le parallélisme n'est pas requis**, en particulier dans les bibliothèques distribuées publiquement. Cela est dû au fait qu'une utilisation de `@async` désactive la migration de la tâche *parent* à travers les threads de travail dans l'implémentation actuelle de Julia. Ainsi, une utilisation apparemment innocente de `@async` dans une fonction de bibliothèque peut avoir un impact important sur les performances de parties très différentes des applications des utilisateurs.


!!! compat "Julia 1.4"
    L'interpolation des valeurs via `$` est disponible depuis Julia 1.4.

