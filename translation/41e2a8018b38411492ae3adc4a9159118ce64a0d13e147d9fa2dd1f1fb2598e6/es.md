```
isready(rr::Future)
```

Determina si un [`Future`](@ref) tiene un valor almacenado.

Si el argumento `Future` es propiedad de un nodo diferente, esta llamada se bloqueará para esperar la respuesta. Se recomienda esperar por `rr` en una tarea separada o usar un [`Channel`](@ref) local como proxy:

```julia
p = 1
f = Future(p)
errormonitor(@async put!(f, remotecall_fetch(long_computation, p)))
isready(f)  # no bloqueará
```
