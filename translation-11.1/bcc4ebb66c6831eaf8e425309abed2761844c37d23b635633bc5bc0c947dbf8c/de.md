```
Threads.threadpoolsize(pool::Symbol = :default) -> Int
```

Erhalten Sie die Anzahl der Threads, die dem Standard-Thread-Pool (oder dem angegebenen Thread-Pool) zur Verfügung stehen.

Siehe auch: `BLAS.get_num_threads` und `BLAS.set_num_threads` in der [`LinearAlgebra`](@ref man-linalg) Standardbibliothek sowie `nprocs()` in der [`Distributed`](@ref man-distributed) Standardbibliothek.
