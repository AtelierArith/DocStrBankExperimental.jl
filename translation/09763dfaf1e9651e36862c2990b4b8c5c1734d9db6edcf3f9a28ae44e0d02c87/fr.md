```
AsyncCondition()
```

Créez une condition asynchrone qui réveille les tâches qui l'attendent (en appelant [`wait`](@ref) sur l'objet) lorsqu'elle est notifiée depuis C par un appel à `uv_async_send`. Les tâches en attente sont réveillées avec une erreur lorsque l'objet est fermé (par [`close`](@ref)). Utilisez [`isopen`](@ref) pour vérifier si elle est toujours active.

Cela fournit un ordre de mémoire implicite d'acquisition et de libération entre les threads d'envoi et d'attente.
