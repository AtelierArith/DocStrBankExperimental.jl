```
task_local_storage(body, key, value)
```

Appelle la fonction `body` avec un stockage local de tâche modifié, dans lequel `value` est assigné à `key`; la valeur précédente de `key`, ou son absence, est restaurée par la suite. Utile pour émuler la portée dynamique.
