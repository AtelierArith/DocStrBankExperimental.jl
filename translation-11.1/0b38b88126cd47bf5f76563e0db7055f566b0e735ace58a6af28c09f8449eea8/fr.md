```
AbstractWorkerPool
```

Supertype pour les pools de travailleurs tels que [`WorkerPool`](@ref) et [`CachingPool`](@ref). Un `AbstractWorkerPool` doit implémenter :

  * [`push!`](@ref) - ajouter un nouveau travailleur au pool global (disponible + occupé)
  * [`put!`](@ref) - remettre un travailleur dans le pool disponible
  * [`take!`](@ref) - prendre un travailleur du pool disponible (à utiliser pour l'exécution de fonctions distantes)
  * [`length`](@ref) - nombre de travailleurs disponibles dans le pool global
  * [`isready`](@ref) - retourner false si un `take!` sur le pool bloquerait, sinon true

Les implémentations par défaut de ce qui précède (sur un `AbstractWorkerPool`) nécessitent des champs

  * `channel::Channel{Int}`
  * `workers::Set{Int}`

où `channel` contient les pids des travailleurs libres et `workers` est l'ensemble de tous les travailleurs associés à ce pool.
