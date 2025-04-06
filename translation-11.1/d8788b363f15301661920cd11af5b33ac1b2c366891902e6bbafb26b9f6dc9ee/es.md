```
take!(c::Channel)
```

Elimina y devuelve un valor de un [`Channel`](@ref) en orden. Bloquea hasta que los datos estén disponibles. Para canales sin búfer, bloquea hasta que se realice un [`put!`](@ref) por otra tarea.

# Ejemplos

Canal con búfer:

```jldoctest
julia> c = Channel(1);

julia> put!(c, 1);

julia> take!(c)
1
```

Canal sin búfer:

```jldoctest
julia> c = Channel(0);

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);

julia> take!(c)
1
```
