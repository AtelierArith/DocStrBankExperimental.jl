```
Threads.nthreads(:default | :interactive) -> Int
```

Obtiene el número actual de hilos dentro del grupo de hilos especificado. Los hilos en `:interactive` tienen números de identificación `1:nthreads(:interactive)`, y los hilos en `:default` tienen números de identificación en `nthreads(:interactive) .+ (1:nthreads(:default))`.

Véase también `BLAS.get_num_threads` y `BLAS.set_num_threads` en la biblioteca estándar [`LinearAlgebra`](@ref man-linalg), y `nprocs()` en la biblioteca estándar [`Distributed`](@ref man-distributed) y [`Threads.maxthreadid()`](@ref).
