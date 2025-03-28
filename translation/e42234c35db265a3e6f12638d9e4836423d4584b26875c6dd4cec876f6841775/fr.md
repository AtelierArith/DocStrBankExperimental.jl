```
manage(manager::ClusterManager, id::Integer, config::WorkerConfig. op::Symbol)
```

Implémenté par les gestionnaires de cluster. Il est appelé sur le processus maître, pendant la durée de vie d'un travailleur, avec des valeurs `op` appropriées :

  * avec `:register`/`:deregister` lorsqu'un travailleur est ajouté / retiré du pool de travailleurs Julia.
  * avec `:interrupt` lorsque `interrupt(workers)` est appelé. Le `ClusterManager` doit signaler au travailleur approprié avec un signal d'interruption.
  * avec `:finalize` à des fins de nettoyage.
