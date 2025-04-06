```
default_worker_pool()
```

[`AbstractWorkerPool`](@ref) boşta olan [`workers`](@ref) içeren - `remote(f)` ve [`pmap`](@ref) (varsayılan olarak) tarafından kullanılır. `default_worker_pool!(pool)` ile açıkça ayarlanmamışsa, varsayılan işçi havuzu bir [`WorkerPool`](@ref) olarak başlatılır.

# Örnekler

```julia-repl
$ julia -p 3

julia> default_worker_pool()
WorkerPool(Channel{Int64}(sz_max:9223372036854775807,sz_curr:3), Set([4, 2, 3]), RemoteChannel{Channel{Any}}(1, 1, 4))
```
