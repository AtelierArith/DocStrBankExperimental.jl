```
launch(manager::ClusterManager, params::Dict, launched::Array, launch_ntfy::Condition)
```

Implementado por administradores de clúster. Para cada trabajador de Julia lanzado por esta función, debe agregar una entrada `WorkerConfig` a `launched` y notificar a `launch_ntfy`. La función DEBE salir una vez que todos los trabajadores, solicitados por `manager`, hayan sido lanzados. `params` es un diccionario de todos los argumentos de palabra clave con los que se llamó a [`addprocs`](@ref).
