```
@task
```

Envuelve una expresión en una [`Task`](@ref) sin ejecutarla, y devuelve la [`Task`](@ref). Esto solo crea una tarea y no la ejecuta.

!!! warning
    Por defecto, las tareas tendrán el bit sticky configurado en true `t.sticky`. Esto modela el comportamiento predeterminado histórico para [`@async`](@ref). Las tareas sticky solo se pueden ejecutar en el hilo de trabajo en el que se programaron por primera vez, y al programarse harán que la tarea desde la cual se programaron sea sticky. Para obtener el comportamiento de [`Threads.@spawn`](@ref), establece el bit sticky manualmente en `false`.


# Ejemplos

```jldoctest
julia> a1() = sum(i for i in 1:1000);

julia> b = @task a1();

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskdone(b)
true
```
