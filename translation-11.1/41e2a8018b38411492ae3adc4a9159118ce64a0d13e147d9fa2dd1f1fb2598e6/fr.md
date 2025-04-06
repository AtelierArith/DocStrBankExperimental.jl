```
isready(rr::Future)
```

Déterminez si un [`Future`](@ref) a une valeur stockée.

Si l'argument `Future` est détenu par un nœud différent, cet appel bloquera en attendant la réponse. Il est recommandé d'attendre `rr` dans une tâche séparée ou d'utiliser un [`Channel`](@ref) local comme proxy :

```julia
p = 1
f = Future(p)
errormonitor(@async put!(f, remotecall_fetch(long_computation, p)))
isready(f)  # ne bloquera pas
```
