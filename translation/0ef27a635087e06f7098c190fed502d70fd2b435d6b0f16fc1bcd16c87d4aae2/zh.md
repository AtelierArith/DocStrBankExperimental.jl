```
default_addprocs_params(mgr::ClusterManager) -> Dict{Symbol, Any}
```

由集群管理器实现。调用 `addprocs(mgr)` 时传递的默认关键字参数。通过调用 `default_addprocs_params()` 可以获得最小选项集。
