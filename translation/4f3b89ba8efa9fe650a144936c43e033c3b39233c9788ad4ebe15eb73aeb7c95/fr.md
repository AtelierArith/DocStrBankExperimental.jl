```
remote([p::AbstractWorkerPool], f) -> Function
```

Retourne une fonction anonyme qui exécute la fonction `f` sur un travailleur disponible (tiré de [`WorkerPool`](@ref) `p` si fourni) en utilisant [`remotecall_fetch`](@ref).
