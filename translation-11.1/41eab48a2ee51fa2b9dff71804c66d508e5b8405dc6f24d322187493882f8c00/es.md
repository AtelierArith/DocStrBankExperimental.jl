```
Timer(delay; interval = 0)
```

Crea un temporizador que despierta tareas que están esperando por él (llamando a [`wait`](@ref) en el objeto temporizador).

Las tareas en espera se despiertan después de un retraso inicial de al menos `delay` segundos, y luego se repiten después de que transcurran al menos `interval` segundos nuevamente. Si `interval` es igual a `0`, el temporizador solo se activa una vez. Cuando el temporizador se cierra (mediante [`close`](@ref)), las tareas en espera se despiertan con un error. Usa [`isopen`](@ref) para verificar si un temporizador sigue activo.

!!! note
    `interval` está sujeto a la acumulación de desajuste de tiempo. Si necesitas eventos precisos en un momento absoluto particular, crea un nuevo temporizador en cada expiración con la diferencia hasta el siguiente tiempo calculada.


!!! note
    Un `Timer` requiere puntos de ceder para actualizar su estado. Por ejemplo, `isopen(t::Timer)` no se puede usar para hacer un timeout en un bucle while que no cede.

