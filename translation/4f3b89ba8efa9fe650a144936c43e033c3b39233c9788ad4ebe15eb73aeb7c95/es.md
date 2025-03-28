```
remote([p::AbstractWorkerPool], f) -> Function
```

Devuelve una función anónima que ejecuta la función `f` en un trabajador disponible (extraído de [`WorkerPool`](@ref) `p` si se proporciona) utilizando [`remotecall_fetch`](@ref).
