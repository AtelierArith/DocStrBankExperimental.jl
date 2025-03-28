```
upstream(ref::GitReference) -> Union{GitReference, Nothing}
```

Déterminez si la branche contenant `ref` a une branche amont spécifiée.

Retournez soit un `GitReference` vers la branche amont si elle existe, soit [`nothing`](@ref) si la branche demandée n'a pas de contrepartie amont.
