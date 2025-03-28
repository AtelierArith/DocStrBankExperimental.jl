```
Threads.threadpoolsize(pool::Symbol = :default) -> Int
```

Obtenez le nombre de threads disponibles pour le pool de threads par défaut (ou pour le pool de threads spécifié).

Voir aussi : `BLAS.get_num_threads` et `BLAS.set_num_threads` dans la bibliothèque standard [`LinearAlgebra`](@ref man-linalg), et `nprocs()` dans la bibliothèque standard [`Distributed`](@ref man-distributed).
