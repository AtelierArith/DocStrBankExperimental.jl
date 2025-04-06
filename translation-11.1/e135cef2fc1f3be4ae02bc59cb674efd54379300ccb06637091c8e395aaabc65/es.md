```
isready(c::Channel)
```

Determina si un [`Channel`](@ref) tiene un valor almacenado en él. Devuelve inmediatamente, no bloquea.

Para canales no bufferizados, devuelve `true` si hay tareas esperando en un [`put!`](@ref).

# Ejemplos

Canal bufferizado:

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> put!(c, 1);

julia> isready(c)
true
```

Canal no bufferizado:

```jldoctest
julia> c = Channel();

julia> isready(c)  # ¡sin tareas esperando para poner!
false

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);  # programa una tarea de put!

julia> isready(c)
true
```
