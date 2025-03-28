```
Threads.nthreads(:default | :interactive) -> Int
```

指定されたスレッドプール内の現在のスレッド数を取得します。`:interactive` のスレッドは `1:nthreads(:interactive)` のID番号を持ち、`:default` のスレッドは `nthreads(:interactive) .+ (1:nthreads(:default))` のID番号を持ちます。

また、[`LinearAlgebra`](@ref man-linalg) 標準ライブラリの `BLAS.get_num_threads` および `BLAS.set_num_threads`、および [`Distributed`](@ref man-distributed) 標準ライブラリの `nprocs()` と [`Threads.maxthreadid()`](@ref) も参照してください。
