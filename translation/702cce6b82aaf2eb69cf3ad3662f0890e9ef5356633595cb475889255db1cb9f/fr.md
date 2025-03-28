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

Voir aussi [Multi-Threading](@ref man-multithreading).

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

Il existe également des paramètres d'ordre de mémoire optionnels pour l'ensemble de fonctions `unsafe`, qui sélectionnent les versions compatibles C/C++ de ces opérations atomiques, si ce paramètre est spécifié à [`unsafe_load`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref), [`unsafe_replace!`](@ref), et [`unsafe_modify!`](@ref).

!!! warning
    Les API suivantes sont obsolètes, bien que le support pour elles devrait rester pendant plusieurs versions.


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

Ces blocs de construction sont utilisés pour créer les objets de synchronisation réguliers.

```@docs
Base.Threads.SpinLock
```
