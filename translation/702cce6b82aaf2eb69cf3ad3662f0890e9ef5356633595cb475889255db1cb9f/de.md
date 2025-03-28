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

Siehe auch [Multi-Threading](@ref man-multithreading).

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

Es gibt auch optionale Parameter zur Speicheranordnung für die `unsafe`-Funktionen, die die C/C++-kompatiblen Versionen dieser atomaren Operationen auswählen, wenn dieser Parameter auf [`unsafe_load`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref), [`unsafe_replace!`](@ref) und [`unsafe_modify!`](@ref) festgelegt ist.

!!! warning
    Die folgenden APIs sind veraltet, obwohl die Unterstützung für sie voraussichtlich in mehreren Versionen erhalten bleibt.


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

Diese Bausteine werden verwendet, um die regulären Synchronisationsobjekte zu erstellen.

```@docs
Base.Threads.SpinLock
```
