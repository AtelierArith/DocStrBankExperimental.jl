# [Multi-Threading](@id lib-multithreading)

```@docs
Base.Threads.@threads
Base.Threads.foreach
Base.Threads.@spawn
Base.Threads.threadid
Base.Threads.maxthreadid
Base.Threads.nthreads
Base.Threads.threadpool
Base.Threads.nthreadpools
Base.Threads.threadpoolsize
Base.Threads.ngcthreads
```

另请参见 [Multi-Threading](@ref man-multithreading)。

## Atomic operations

```@docs
atomic
```

```@docs
Base.@atomic
Base.@atomicswap
Base.@atomicreplace
Base.@atomiconce
Base.AtomicMemory
```

还有可选的内存排序参数用于 `unsafe` 函数集，如果指定该参数，将选择与 C/C++ 兼容的这些原子操作版本，具体包括 [`unsafe_load`](@ref)、[`unsafe_store!`](@ref)、[`unsafe_swap!`](@ref)、[`unsafe_replace!`](@ref) 和 [`unsafe_modify!`](@ref)。

!!! warning
    以下API已被弃用，但对它们的支持可能会在多个版本中继续存在。


```@docs
Base.Threads.Atomic
Base.Threads.atomic_cas!
Base.Threads.atomic_xchg!
Base.Threads.atomic_add!
Base.Threads.atomic_sub!
Base.Threads.atomic_and!
Base.Threads.atomic_nand!
Base.Threads.atomic_or!
Base.Threads.atomic_xor!
Base.Threads.atomic_max!
Base.Threads.atomic_min!
Base.Threads.atomic_fence
```

## ccall using a libuv threadpool (Experimental)

```@docs
Base.@threadcall
```

## Low-level synchronization primitives

这些构建块用于创建常规同步对象。

```@docs
Base.Threads.SpinLock
```
