```
bind(chnl::Channel, task::Task)
```

Asocia la duración de `chnl` con una tarea. `Channel` `chnl` se cierra automáticamente cuando la tarea termina. Cualquier excepción no capturada en la tarea se propaga a todos los que están a la espera en `chnl`.

El objeto `chnl` se puede cerrar explícitamente independientemente de la terminación de la tarea. Las tareas que terminan no tienen efecto en los objetos `Channel` que ya están cerrados.

Cuando un canal está vinculado a múltiples tareas, la primera tarea que termine cerrará el canal. Cuando múltiples canales están vinculados a la misma tarea, la terminación de la tarea cerrará todos los canales vinculados.

# Ejemplos

```jldoctest
julia> c = Channel(0);

julia> task = @async foreach(i->put!(c, i), 1:4);

julia> bind(c,task);

julia> for i in c
           @show i
       end;
i = 1
i = 2
i = 3
i = 4

julia> isopen(c)
false
```

```jldoctest
julia> c = Channel(0);

julia> task = @async (put!(c, 1); error("foo"));

julia> bind(c, task);

julia> take!(c)
1

julia> put!(c, 1);
ERROR: TaskFailedException
Stacktrace:
[...]
    nested task error: foo
[...]
```
