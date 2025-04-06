```
remotecall_wait(f, id::Integer, args...; kwargs...)
```

Realiza un `wait(remotecall(...))` más rápido en un solo mensaje en el `Worker` especificado por el id de trabajador `id`. Los argumentos de palabra clave, si los hay, se pasan a `f`.

Consulta también [`wait`](@ref) y [`remotecall`](@ref).
