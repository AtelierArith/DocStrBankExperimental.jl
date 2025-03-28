```
Threads.nthreads(:default | :interactive) -> Int
```

Obtenez le nombre actuel de threads dans le pool de threads spécifié. Les threads dans `:interactive` ont des numéros d'identification `1:nthreads(:interactive)`, et les threads dans `:default` ont des numéros d'identification dans `nthreads(:interactive) .+ (1:nthreads(:default))`.

Voir aussi `BLAS.get_num_threads` et `BLAS.set_num_threads` dans la bibliothèque standard [`LinearAlgebra`](@ref man-linalg), et `nprocs()` dans la bibliothèque standard [`Distributed`](@ref man-distributed) et [`Threads.maxthreadid()`](@ref).
