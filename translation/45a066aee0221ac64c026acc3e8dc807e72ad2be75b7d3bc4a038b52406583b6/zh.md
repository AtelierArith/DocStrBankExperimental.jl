```
Threads.nthreads(:default | :interactive) -> Int
```

获取指定线程池中当前的线程数量。`:interactive` 中的线程具有 id 编号 `1:nthreads(:interactive)`，而 `:default` 中的线程具有 id 编号 `nthreads(:interactive) .+ (1:nthreads(:default))`。

另请参见 [`BLAS.get_num_threads`] 和 [`BLAS.set_num_threads`] 在 [`LinearAlgebra`](@ref man-linalg) 标准库中，以及 [`nprocs()`] 在 [`Distributed`](@ref man-distributed) 标准库和 [`Threads.maxthreadid()`](@ref)。
