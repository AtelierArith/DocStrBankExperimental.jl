```
schedule(t::Task, [val]; error=false)
```

Ajoute une [`Task`](@ref) à la file d'attente du planificateur. Cela fait en sorte que la tâche s'exécute constamment lorsque le système est autrement inactif, à moins que la tâche n'effectue une opération bloquante telle que [`wait`](@ref).

Si un deuxième argument `val` est fourni, il sera passé à la tâche (via la valeur de retour de [`yieldto`](@ref)) lorsqu'elle s'exécute à nouveau. Si `error` est `true`, la valeur est levée comme une exception dans la tâche réveillée.

!!! warning
    Il est incorrect d'utiliser `schedule` sur une `Task` arbitraire qui a déjà été démarrée. Voir [la référence API](@ref low-level-schedule-wait) pour plus d'informations.


!!! warning
    Par défaut, les tâches auront le bit collant défini sur vrai `t.sticky`. Cela modélise le comportement par défaut historique pour [`@async`](@ref). Les tâches collantes ne peuvent être exécutées que sur le fil de travail sur lequel elles ont été d'abord planifiées, et lorsqu'elles sont planifiées, elles rendront la tâche à partir de laquelle elles ont été planifiées collante. Pour obtenir le comportement de [`Threads.@spawn`](@ref), définissez manuellement le bit collant sur `false`.


# Exemples

```jldoctest
julia> a5() = sum(i for i in 1:1000);

julia> b = Task(a5);

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskstarted(b)
true

julia> istaskdone(b)
true
```
