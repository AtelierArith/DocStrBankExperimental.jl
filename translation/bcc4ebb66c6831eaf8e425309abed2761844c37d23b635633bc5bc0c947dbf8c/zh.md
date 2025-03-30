```
Threads.threadpoolsize(pool::Symbol = :default) -> Int
```

获取可用于默认线程池（或指定线程池）的线程数量。

另请参见标准库中的 `BLAS.get_num_threads` 和 `BLAS.set_num_threads`，以及 [`Distributed`](@ref man-distributed) 标准库中的 `nprocs()`。
