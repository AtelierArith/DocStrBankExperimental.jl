```
put!(c::Channel, v)
```

Agrega un elemento `v` al canal `c`. Bloquea si el canal está lleno.

Para canales no almacenados, bloquea hasta que se realice un [`take!`](@ref) por otra tarea.

!!! compat "Julia 1.1"
    `v` ahora se convierte al tipo del canal con [`convert`](@ref) cuando se llama a `put!`.

