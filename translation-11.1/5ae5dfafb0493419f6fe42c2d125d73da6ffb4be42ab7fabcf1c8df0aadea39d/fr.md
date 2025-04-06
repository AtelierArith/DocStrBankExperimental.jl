```
default_worker_pool()
```

[`AbstractWorkerPool`](@ref) contenant des [`workers`](@ref) inactifs - utilisé par `remote(f)` et [`pmap`](@ref) (par défaut). À moins qu'un ne soit explicitement défini via `default_worker_pool!(pool)`, le pool de travailleurs par défaut est initialisé à un [`WorkerPool`](@ref).

# Exemples

```julia-repl
$ julia -p 3

julia> default_worker_pool()
WorkerPool(Channel{Int64}(sz_max:9223372036854775807,sz_curr:3), Set([4, 2, 3]), RemoteChannel{Channel{Any}}(1, 1, 4))
```
