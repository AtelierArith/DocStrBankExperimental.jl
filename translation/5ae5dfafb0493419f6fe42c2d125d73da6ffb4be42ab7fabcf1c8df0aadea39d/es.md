```
default_worker_pool()
```

[`AbstractWorkerPool`](@ref) que contiene [`workers`](@ref) inactivos - utilizado por `remote(f)` y [`pmap`](@ref) (por defecto). A menos que se establezca explícitamente a través de `default_worker_pool!(pool)`, el grupo de trabajadores predeterminado se inicializa a un [`WorkerPool`](@ref).

# Ejemplos

```julia-repl
$ julia -p 3

julia> default_worker_pool()
WorkerPool(Channel{Int64}(sz_max:9223372036854775807,sz_curr:3), Set([4, 2, 3]), RemoteChannel{Channel{Any}}(1, 1, 4))
```
