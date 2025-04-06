```
@task
```

Enveloppez une expression dans une [`Task`](@ref) sans l'exécuter, et renvoyez la [`Task`](@ref). Cela crée uniquement une tâche, et ne l'exécute pas.

!!! avertissement
    Par défaut, les tâches auront le bit collant défini sur true `t.sticky`. Cela modélise le comportement par défaut historique pour [`@async`](@ref). Les tâches collantes ne peuvent être exécutées que sur le fil de travail sur lequel elles ont été d'abord planifiées, et lorsqu'elles sont planifiées, elles rendront la tâche à partir de laquelle elles ont été planifiées collante. Pour obtenir le comportement de [`Threads.@spawn`](@ref), définissez manuellement le bit collant sur `false`.


# Exemples

```jldoctest
julia> a1() = sum(i for i in 1:1000);

julia> b = @task a1();

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskdone(b)
true
```
