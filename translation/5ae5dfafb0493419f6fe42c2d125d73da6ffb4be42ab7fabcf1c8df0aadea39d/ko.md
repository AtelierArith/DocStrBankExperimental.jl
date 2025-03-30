```
default_worker_pool()
```

[`AbstractWorkerPool`](@ref)는 유휴 [`workers`](@ref)를 포함하고 있으며, `remote(f)` 및 [`pmap`](@ref) (기본적으로)에서 사용됩니다. `default_worker_pool!(pool)`을 통해 명시적으로 설정되지 않는 한, 기본 작업자 풀은 [`WorkerPool`](@ref)로 초기화됩니다.

# 예제

```julia-repl
$ julia -p 3

julia> default_worker_pool()
WorkerPool(Channel{Int64}(sz_max:9223372036854775807,sz_curr:3), Set([4, 2, 3]), RemoteChannel{Channel{Any}}(1, 1, 4))
```
