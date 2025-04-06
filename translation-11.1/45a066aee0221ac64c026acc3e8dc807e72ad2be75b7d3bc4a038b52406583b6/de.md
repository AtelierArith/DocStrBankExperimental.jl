```
Threads.nthreads(:default | :interactive) -> Int
```

Holen Sie sich die aktuelle Anzahl der Threads im angegebenen Thread-Pool. Die Threads in `:interactive` haben ID-Nummern `1:nthreads(:interactive)`, und die Threads in `:default` haben ID-Nummern in `nthreads(:interactive) .+ (1:nthreads(:default))`.

Siehe auch `BLAS.get_num_threads` und `BLAS.set_num_threads` in der [`LinearAlgebra`](@ref man-linalg) Standardbibliothek, und `nprocs()` in der [`Distributed`](@ref man-distributed) Standardbibliothek und [`Threads.maxthreadid()`](@ref).
