```
AsyncCondition()
```

Crea una condición asíncrona que despierta tareas que están esperando por ella (llamando a [`wait`](@ref) en el objeto) cuando se notifica desde C mediante una llamada a `uv_async_send`. Las tareas en espera se despiertan con un error cuando el objeto se cierra (mediante [`close`](@ref)). Usa [`isopen`](@ref) para verificar si todavía está activa.

Esto proporciona un orden de memoria implícito de adquisición y liberación entre los hilos que envían y los que esperan.
