```
Threads.maxthreadid() -> Int
```

Obtenez une limite inférieure sur le nombre de threads (dans tous les pools de threads) disponibles pour le processus Julia, avec des sémantiques d'acquisition atomique. Le résultat sera toujours supérieur ou égal à [`threadid()`](@ref) ainsi qu'à `threadid(task)` pour toute tâche que vous avez pu observer avant d'appeler `maxthreadid`.
