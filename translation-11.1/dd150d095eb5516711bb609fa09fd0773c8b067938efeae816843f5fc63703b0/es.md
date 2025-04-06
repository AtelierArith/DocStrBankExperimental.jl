```
Threads.@spawn [:default|:interactive] expr
```

Crea una [`Task`](@ref) y la [`schedule`](@ref) para que se ejecute en cualquier hilo disponible en el grupo de hilos especificado (`:default` si no se especifica). La tarea se asigna a un hilo una vez que uno se vuelve disponible. Para esperar a que la tarea termine, llama a [`wait`](@ref) sobre el resultado de este macro, o llama a [`fetch`](@ref) para esperar y luego obtener su valor de retorno.

Los valores se pueden interpolar en `@spawn` a través de `$`, que copia el valor directamente en el cierre subyacente construido. Esto te permite insertar el *valor* de una variable, aislando el código asíncrono de los cambios en el valor de la variable en la tarea actual.

!!! note
    El hilo en el que se ejecuta la tarea puede cambiar si la tarea cede, por lo tanto, `threadid()` no debe ser tratado como constante para una tarea. Consulta [`Task Migration`](@ref man-task-migration), y el manual más amplio de [multi-threading](@ref man-multithreading) para más advertencias importantes. Consulta también el capítulo sobre [threadpools](@ref man-threadpools).


!!! compat "Julia 1.3"
    Este macro está disponible desde Julia 1.3.


!!! compat "Julia 1.4"
    La interpolación de valores a través de `$` está disponible desde Julia 1.4.


!!! compat "Julia 1.9"
    Se puede especificar un grupo de hilos desde Julia 1.9.


# Ejemplos

```julia-repl
julia> t() = println("Hello from ", Threads.threadid());

julia> tasks = fetch.([Threads.@spawn t() for i in 1:4]);
Hello from 1
Hello from 1
Hello from 3
Hello from 4
```
