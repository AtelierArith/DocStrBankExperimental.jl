```
upstream(ref::GitReference) -> Union{GitReference, Nothing}
```

Determina si la rama que contiene `ref` tiene una rama upstream especificada.

Devuelve ya sea un `GitReference` a la rama upstream si existe, o [`nothing`](@ref) si la rama solicitada no tiene un contraparte upstream.
