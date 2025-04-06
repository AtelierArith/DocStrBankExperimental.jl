```
put!(rr::RemoteChannel, args...)
```

Stocke un ensemble de valeurs dans le [`RemoteChannel`](@ref). Si le canal est plein, il bloque jusqu'à ce qu'un espace soit disponible. Retourne le premier argument.
