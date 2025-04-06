```
Condition()
```

Créez une source d'événements déclenchée par un bord sur laquelle les tâches peuvent attendre. Les tâches qui appellent [`wait`](@ref) sur un `Condition` sont suspendues et mises en file d'attente. Les tâches sont réveillées lorsque [`notify`](@ref) est appelé plus tard sur le `Condition`. Attendre sur une condition peut renvoyer une valeur ou lever une erreur si les arguments optionnels de [`notify`](@ref) sont utilisés. Le déclenchement par bord signifie que seules les tâches en attente au moment où [`notify`](@ref) est appelé peuvent être réveillées. Pour des notifications déclenchées par niveau, vous devez conserver un état supplémentaire pour suivre si une notification a eu lieu. Les types [`Channel`](@ref) et [`Threads.Event`](@ref) le font et peuvent être utilisés pour des événements déclenchés par niveau.

Cet objet n'est PAS sûr pour les threads. Voir [`Threads.Condition`](@ref) pour une version sûre pour les threads.
