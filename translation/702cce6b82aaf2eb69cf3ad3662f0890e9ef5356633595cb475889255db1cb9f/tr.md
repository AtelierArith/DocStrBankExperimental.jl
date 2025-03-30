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

Ayrıca [Multi-Threading](@ref man-multithreading)'e bakın.

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

`unsafe` setindeki işlevler için, bu atomik işlemlerin C/C++ uyumlu sürümlerini seçen isteğe bağlı bellek sıralama parametreleri de vardır; eğer bu parametre [`unsafe_load`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref), [`unsafe_replace!`](@ref) ve [`unsafe_modify!`](@ref) olarak belirtilirse.

!!! warning
    Aşağıdaki API'ler kullanımdan kaldırılmıştır, ancak bunlar için destek muhtemelen birkaç sürüm boyunca devam edecektir.


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

Bu yapı taşları, düzenli senkronizasyon nesnelerini oluşturmak için kullanılır.

```@docs
Base.Threads.SpinLock
```
