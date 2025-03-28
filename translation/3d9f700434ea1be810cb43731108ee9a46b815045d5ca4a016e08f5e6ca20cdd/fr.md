```
notify(condition, val=nothing; all=true, error=false)
```

Réveille les tâches en attente d'une condition, en leur passant `val`. Si `all` est `true` (par défaut), toutes les tâches en attente sont réveillées, sinon une seule l'est. Si `error` est `true`, la valeur passée est levée comme une exception dans les tâches réveillées.

Retourne le nombre de tâches réveillées. Retourne 0 si aucune tâche n'attend sur `condition`.
