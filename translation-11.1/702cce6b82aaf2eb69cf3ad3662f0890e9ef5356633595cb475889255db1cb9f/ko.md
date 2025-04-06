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

또한 [Multi-Threading](@ref man-multithreading)를 참조하세요.

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

`unsafe` 함수 집합에 대한 선택적 메모리 정렬 매개변수가 있으며, 이 매개변수가 지정되면 이러한 원자적 작업의 C/C++ 호환 버전을 선택합니다. 매개변수는 다음과 같습니다: [`unsafe_load`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref), [`unsafe_replace!`](@ref), 및 [`unsafe_modify!`](@ref).

!!! warning
    다음 API는 더 이상 사용되지 않지만, 여러 릴리스 동안 지원이 유지될 가능성이 높습니다.


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

이 빌딩 블록은 정기적인 동기화 객체를 생성하는 데 사용됩니다.

```@docs
Base.Threads.SpinLock
```
