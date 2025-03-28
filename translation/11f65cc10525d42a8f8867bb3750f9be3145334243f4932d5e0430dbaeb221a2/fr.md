```
Event([autoreset=false])
```

Créez une source d'événement à déclenchement de niveau. Les tâches qui appellent [`wait`](@ref) sur un `Event` sont suspendues et mises en file d'attente jusqu'à ce que [`notify`](@ref) soit appelé sur l'`Event`. Après que `notify` a été appelé, l'`Event` reste dans un état signalé et les tâches ne bloqueront plus en attendant, jusqu'à ce que `reset` soit appelé.

Si `autoreset` est vrai, au maximum une tâche sera libérée de `wait` pour chaque appel à `notify`.

Cela fournit un ordre de mémoire d'acquisition et de libération sur notify/wait.

!!! compat "Julia 1.1"
    Cette fonctionnalité nécessite au moins Julia 1.1.


!!! compat "Julia 1.8"
    La fonctionnalité `autoreset` et la garantie d'ordre de mémoire nécessitent au moins Julia 1.8.

