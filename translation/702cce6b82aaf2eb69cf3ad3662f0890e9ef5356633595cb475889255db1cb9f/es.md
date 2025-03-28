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

Véase también [Multi-Threading](@ref man-multithreading).

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

También hay parámetros opcionales de ordenamiento de memoria para el conjunto de funciones `unsafe`, que seleccionan las versiones de estas operaciones atómicas compatibles con C/C++, si ese parámetro se especifica a [`unsafe_load`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref), [`unsafe_replace!`](@ref), y [`unsafe_modify!`](@ref).

!!! warning
    Las siguientes API están en desuso, aunque es probable que el soporte para ellas permanezca durante varias versiones.


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

Estos bloques de construcción se utilizan para crear los objetos de sincronización regulares.

```@docs
Base.Threads.SpinLock
```
