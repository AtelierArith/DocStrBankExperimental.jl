```
Threads.nthreads(:default | :interactive) -> Int
```

Belirtilen iş parçacığı havuzundaki mevcut iş parçacığı sayısını alır. `:interactive` içindeki iş parçacıkları `1:nthreads(:interactive)` kimlik numaralarına sahiptir ve `:default` içindeki iş parçacıkları `nthreads(:interactive) .+ (1:nthreads(:default))` kimlik numaralarına sahiptir.

Ayrıca [`LinearAlgebra`](@ref man-linalg) standart kütüphanesindeki `BLAS.get_num_threads` ve `BLAS.set_num_threads` ile [`Distributed`](@ref man-distributed) standart kütüphanesindeki `nprocs()` ve [`Threads.maxthreadid()`](@ref) ile de bakabilirsiniz.
