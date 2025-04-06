```
Task(func)
```

Créez une `Task` (c'est-à-dire une coroutine) pour exécuter la fonction donnée `func` (qui doit être appelable sans arguments). La tâche se termine lorsque cette fonction retourne. La tâche s'exécutera dans l'"âge du monde" du parent au moment de la construction lors de la planification [`schedule`](@ref).

!!! avertissement
    Par défaut, les tâches auront le bit collant défini sur true `t.sticky`. Cela modélise le comportement par défaut historique pour [`@async`](@ref). Les tâches collantes ne peuvent être exécutées que sur le fil de travail sur lequel elles ont été d'abord planifiées, et lorsqu'elles sont planifiées, elles rendront la tâche à partir de laquelle elles ont été planifiées collante. Pour obtenir le comportement de [`Threads.@spawn`](@ref), définissez manuellement le bit collant sur `false`.


# Exemples

```jldoctest
julia> a() = sum(i for i in 1:1000);

julia> b = Task(a);
```

Dans cet exemple, `b` est une `Task` exécutable qui n'a pas encore commencé.
