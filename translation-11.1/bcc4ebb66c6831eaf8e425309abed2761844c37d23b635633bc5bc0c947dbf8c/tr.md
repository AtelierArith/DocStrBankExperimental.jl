```
Threads.threadpoolsize(pool::Symbol = :default) -> Int
```

Varsayılan iş parçacığı havuzuna (veya belirtilen iş parçacığı havuzuna) mevcut olan iş parçacığı sayısını alır.

Ayrıca bkz: `BLAS.get_num_threads` ve `BLAS.set_num_threads` [`LinearAlgebra`](@ref man-linalg) standart kütüphanesinde, ve `nprocs()` [`Distributed`](@ref man-distributed) standart kütüphanesinde.
