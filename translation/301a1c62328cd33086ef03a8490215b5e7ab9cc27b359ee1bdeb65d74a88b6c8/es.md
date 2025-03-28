```
istaskfailed(t::Task) -> Bool
```

Determina si una tarea ha salido porque se lanzó una excepción.

# Ejemplos

```jldoctest
julia> a4() = error("tarea fallida");

julia> b = Task(a4);

julia> istaskfailed(b)
false

julia> schedule(b);

julia> yield();

julia> istaskfailed(b)
true
```

!!! compat "Julia 1.3"
    Esta función requiere al menos Julia 1.3.

