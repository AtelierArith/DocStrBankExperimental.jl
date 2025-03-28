```
istaskfailed(t::Task) -> Bool
```

Détermine si une tâche a quitté en raison d'une exception lancée.

# Exemples

```jldoctest
julia> a4() = error("tâche échouée");

julia> b = Task(a4);

julia> istaskfailed(b)
false

julia> schedule(b);

julia> yield();

julia> istaskfailed(b)
true
```

!!! compat "Julia 1.3"
    Cette fonction nécessite au moins Julia 1.3.

