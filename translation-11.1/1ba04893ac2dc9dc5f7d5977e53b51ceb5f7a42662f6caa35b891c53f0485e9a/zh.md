```
LinearAlgebra.peakflops(n::Integer=4096; eltype::DataType=Float64, ntrials::Integer=3, parallel::Bool=false)
```

`peakflops` 通过使用双精度 [`gemm!`](@ref LinearAlgebra.BLAS.gemm!) 计算计算机的峰值浮点运算速率。默认情况下，如果未指定任何参数，它将乘以两个大小为 `n x n` 的 `Float64` 矩阵，其中 `n = 4096`。如果底层的 BLAS 使用多个线程，则可以实现更高的浮点运算速率。BLAS 线程的数量可以通过 [`BLAS.set_num_threads(n)`](@ref) 设置。

如果提供了关键字参数 `eltype`，`peakflops` 将构造具有类型 `eltype` 的元素的矩阵以计算峰值浮点运算速率。

默认情况下，`peakflops` 将使用 3 次试验中的最佳计时。如果提供了关键字参数 `ntrials`，`peakflops` 将使用指定的试验次数来选择最佳计时。

如果关键字参数 `parallel` 设置为 `true`，`peakflops` 将在所有工作处理器上并行运行。将返回整个并行计算机的浮点运算速率。在并行运行时，仅使用 1 个 BLAS 线程。参数 `n` 仍然指的是在每个处理器上解决的问题的大小。

!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。在 Julia 1.0 中，它可以从标准库 `InteractiveUtils` 中获得。

