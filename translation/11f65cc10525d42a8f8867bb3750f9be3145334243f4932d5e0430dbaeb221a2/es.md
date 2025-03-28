```
Event([autoreset=false])
```

Crea una fuente de eventos activada por nivel. Las tareas que llaman a [`wait`](@ref) en un `Event` son suspendidas y encoladas hasta que se llame a [`notify`](@ref) en el `Event`. Después de que se llama a `notify`, el `Event` permanece en un estado señalizado y las tareas ya no se bloquearán al esperar por él, hasta que se llame a `reset`.

Si `autoreset` es verdadero, como máximo una tarea será liberada de `wait` por cada llamada a `notify`.

Esto proporciona un orden de memoria de adquisición y liberación en notify/wait.

!!! compat "Julia 1.1"
    Esta funcionalidad requiere al menos Julia 1.1.


!!! compat "Julia 1.8"
    La funcionalidad de `autoreset` y la garantía de orden de memoria requieren al menos Julia 1.8.

