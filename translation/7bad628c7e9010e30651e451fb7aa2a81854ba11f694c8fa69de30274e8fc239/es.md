```
Task(func)
```

Crea un `Task` (es decir, una coroutine) para ejecutar la función dada `func` (que debe ser invocable sin argumentos). La tarea finaliza cuando esta función retorna. La tarea se ejecutará en la "edad del mundo" del padre en el momento de la construcción cuando se [`schedule`](@ref)d.

!!! warning
    Por defecto, las tareas tendrán el bit sticky configurado en true `t.sticky`. Esto modela el comportamiento predeterminado histórico para [`@async`](@ref). Las tareas sticky solo pueden ejecutarse en el hilo de trabajo en el que fueron programadas por primera vez, y al ser programadas harán que la tarea desde la cual fueron programadas sea sticky. Para obtener el comportamiento de [`Threads.@spawn`](@ref), establece el bit sticky manualmente en `false`.


# Ejemplos

```jldoctest
julia> a() = sum(i for i in 1:1000);

julia> b = Task(a);
```

En este ejemplo, `b` es un `Task` ejecutable que aún no ha comenzado.
