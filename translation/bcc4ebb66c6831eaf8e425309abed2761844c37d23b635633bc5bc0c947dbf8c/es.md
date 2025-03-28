```
Threads.threadpoolsize(pool::Symbol = :default) -> Int
```

Obtiene el número de hilos disponibles en el grupo de hilos predeterminado (o en el grupo de hilos especificado).

Véase también: `BLAS.get_num_threads` y `BLAS.set_num_threads` en la biblioteca estándar [`LinearAlgebra`](@ref man-linalg), y `nprocs()` en la biblioteca estándar [`Distributed`](@ref man-distributed).
