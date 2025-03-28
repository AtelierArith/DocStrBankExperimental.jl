```
default_addprocs_params(mgr::ClusterManager) -> Dict{Symbol, Any}
```

Implémenté par les gestionnaires de cluster. Les paramètres de mot-clé par défaut passés lors de l'appel de `addprocs(mgr)`. L'ensemble minimal d'options est disponible en appelant `default_addprocs_params()`.
