```
istaskstarted(t::Task) -> Bool
```

Déterminez si une tâche a commencé à s'exécuter.

# Exemples

```jldoctest
julia> a3() = sum(i for i in 1:1000);

julia> b = Task(a3);

julia> istaskstarted(b)
false
```
