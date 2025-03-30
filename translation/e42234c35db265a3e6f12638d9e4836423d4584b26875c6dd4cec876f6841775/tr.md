```
manage(manager::ClusterManager, id::Integer, config::WorkerConfig. op::Symbol)
```

Küme yöneticileri tarafından uygulanır. Bir işçi süresi boyunca ana süreçte, uygun `op` değerleri ile çağrılır:

  * Bir işçi Julia işçi havuzuna eklendiğinde / kaldırıldığında `:register`/`:deregister` ile.
  * `interrupt(workers)` çağrıldığında `:interrupt` ile. `ClusterManager`, uygun işçiye bir kesme sinyali göndermelidir.
  * Temizlik amaçları için `:finalize` ile.
