```
default_addprocs_params(mgr::ClusterManager) -> Dict{Symbol, Any}
```

Implementiert von Cluster-Managern. Die Standard-Keyword-Parameter, die beim Aufruf von `addprocs(mgr)` übergeben werden. Die minimale Menge an Optionen ist verfügbar, indem `default_addprocs_params()` aufgerufen wird.
