```
schedule(t::Task, [val]; error=false)
```

Agrega un [`Task`](@ref) a la cola del programador. Esto hace que la tarea se ejecute constantemente cuando el sistema está inactivo, a menos que la tarea realice una operación de bloqueo como [`wait`](@ref).

Si se proporciona un segundo argumento `val`, se pasará a la tarea (a través del valor de retorno de [`yieldto`](@ref)) cuando se ejecute nuevamente. Si `error` es `true`, el valor se levantará como una excepción en la tarea despertada.

!!! warning
    Es incorrecto usar `schedule` en un `Task` arbitrario que ya ha sido iniciado. Consulta [la referencia de la API](@ref low-level-schedule-wait) para más información.


!!! warning
    Por defecto, las tareas tendrán el bit sticky configurado en true `t.sticky`. Esto modela el comportamiento predeterminado histórico para [`@async`](@ref). Las tareas sticky solo se pueden ejecutar en el hilo de trabajo en el que se programaron por primera vez, y al programarse harán que la tarea desde la que se programaron sea sticky. Para obtener el comportamiento de [`Threads.@spawn`](@ref), establece el bit sticky manualmente en `false`.


# Ejemplos

```jldoctest
julia> a5() = sum(i for i in 1:1000);

julia> b = Task(a5);

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskstarted(b)
true

julia> istaskdone(b)
true
```
