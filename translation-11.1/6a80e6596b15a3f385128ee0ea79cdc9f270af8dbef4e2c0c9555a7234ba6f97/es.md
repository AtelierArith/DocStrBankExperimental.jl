```
Condition()
```

Crea una fuente de eventos activada por bordes que las tareas pueden esperar. Las tareas que llaman a [`wait`](@ref) en un `Condition` son suspendidas y encoladas. Las tareas se despiertan cuando se llama a [`notify`](@ref) más tarde en el `Condition`. Esperar en una condición puede devolver un valor o generar un error si se utilizan los argumentos opcionales de [`notify`](@ref). La activación por bordes significa que solo las tareas que están esperando en el momento en que se llama a [`notify`](@ref) pueden ser despertadas. Para notificaciones activadas por niveles, debes mantener un estado adicional para hacer un seguimiento de si ha ocurrido una notificación. Los tipos [`Channel`](@ref) y [`Threads.Event`](@ref) hacen esto y se pueden usar para eventos activados por niveles.

Este objeto NO es seguro para hilos. Consulta [`Threads.Condition`](@ref) para una versión segura para hilos.
