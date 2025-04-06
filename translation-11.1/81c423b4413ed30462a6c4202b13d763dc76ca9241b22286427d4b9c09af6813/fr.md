```
istaskdone(t::Task) -> Bool
```

Déterminez si une tâche a quitté.

# Exemples

```jldoctest
julia> a2() = sum(i for i in 1:1000);

julia> b = Task(a2);

julia> istaskdone(b)
false

julia> schedule(b);

julia> yield();

julia> istaskdone(b)
true
```
