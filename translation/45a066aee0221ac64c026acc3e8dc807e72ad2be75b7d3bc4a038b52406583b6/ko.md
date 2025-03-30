```
Threads.nthreads(:default | :interactive) -> Int
```

지정된 스레드 풀 내에서 현재 스레드 수를 가져옵니다. `:interactive`의 스레드는 ID 번호가 `1:nthreads(:interactive)`이고, `:default`의 스레드는 ID 번호가 `nthreads(:interactive) .+ (1:nthreads(:default))`입니다.

또한 [`LinearAlgebra`](@ref man-linalg) 표준 라이브러리의 `BLAS.get_num_threads` 및 `BLAS.set_num_threads`, 그리고 [`Distributed`](@ref man-distributed) 표준 라이브러리의 `nprocs()` 및 [`Threads.maxthreadid()`](@ref)를 참조하십시오.
