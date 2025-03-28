```
istaskstarted(t::Task) -> Bool
```

Determina si una tarea ha comenzado a ejecutarse.

# Ejemplos

```jldoctest
julia> a3() = sum(i for i in 1:1000);

julia> b = Task(a3);

julia> istaskstarted(b)
false
```
