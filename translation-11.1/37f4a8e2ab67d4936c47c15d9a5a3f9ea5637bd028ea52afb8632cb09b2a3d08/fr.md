```
launch(manager::ClusterManager, params::Dict, launched::Array, launch_ntfy::Condition)
```

Implémenté par les gestionnaires de cluster. Pour chaque travailleur Julia lancé par cette fonction, il doit ajouter une entrée `WorkerConfig` à `launched` et notifier `launch_ntfy`. La fonction DOIT se terminer une fois que tous les travailleurs, demandés par `manager`, ont été lancés. `params` est un dictionnaire de tous les arguments de mot-clé avec lesquels [`addprocs`](@ref) a été appelé.
