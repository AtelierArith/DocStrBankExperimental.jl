```
manage(manager::ClusterManager, id::Integer, config::WorkerConfig. op::Symbol)
```

Implementado por los administradores de clúster. Se llama en el proceso maestro, durante la vida útil de un trabajador, con los valores `op` apropiados:

  * con `:register`/`:deregister` cuando un trabajador es agregado / eliminado del grupo de trabajadores de Julia.
  * con `:interrupt` cuando se llama a `interrupt(workers)`. El `ClusterManager` debe señalizar al trabajador apropiado con una señal de interrupción.
  * con `:finalize` para propósitos de limpieza.
