```
Threads.threadpoolsize(pool::Symbol = :default) -> Int
```

기본 스레드 풀(또는 지정된 스레드 풀)에 사용할 수 있는 스레드 수를 가져옵니다.

또한, [`LinearAlgebra`](@ref man-linalg) 표준 라이브러리의 `BLAS.get_num_threads` 및 `BLAS.set_num_threads`, 그리고 [`Distributed`](@ref man-distributed) 표준 라이브러리의 `nprocs()`를 참조하십시오.
