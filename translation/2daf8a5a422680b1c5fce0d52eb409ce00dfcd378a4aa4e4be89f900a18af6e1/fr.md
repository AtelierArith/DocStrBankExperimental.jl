```
CFunction struct
```

Gestion de la collecte des déchets pour la valeur de retour de `@cfunction` lorsque le premier argument est annoté avec '$'. Comme tous les handles `cfunction`, il doit être passé à `ccall` en tant que `Ptr{Cvoid}`, et sera converti automatiquement au site d'appel au type approprié.

Voir [`@cfunction`](@ref).
