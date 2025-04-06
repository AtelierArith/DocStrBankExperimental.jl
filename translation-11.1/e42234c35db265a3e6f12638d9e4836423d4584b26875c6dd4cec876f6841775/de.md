```
manage(manager::ClusterManager, id::Integer, config::WorkerConfig. op::Symbol)
```

Implementiert von Cluster-Managern. Es wird im Master-Prozess während der Lebensdauer eines Workers mit den entsprechenden `op`-Werten aufgerufen:

  * mit `:register`/`:deregister`, wenn ein Worker zum Julia-Worker-Pool hinzugefügt / entfernt wird.
  * mit `:interrupt`, wenn `interrupt(workers)` aufgerufen wird. Der `ClusterManager` sollte den entsprechenden Worker mit einem Interrupt-Signal benachrichtigen.
  * mit `:finalize` zu Reinigungszwecken.
