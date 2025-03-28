```
default_worker_pool()
```

[`AbstractWorkerPool`](@ref) mit inaktiven [`workers`](@ref) - verwendet von `remote(f)` und [`pmap`](@ref) (standardmäßig). Es sei denn, es wird explizit über `default_worker_pool!(pool)` festgelegt, wird der Standard-Worker-Pool auf einen [`WorkerPool`](@ref) initialisiert.

# Beispiele

```julia-repl
$ julia -p 3

julia> default_worker_pool()
WorkerPool(Channel{Int64}(sz_max:9223372036854775807,sz_curr:3), Set([4, 2, 3]), RemoteChannel{Channel{Any}}(1, 1, 4))
```
