```
@sync
```

모든 어휘적으로 포함된 [`@async`](@ref), [`@spawn`](@ref Threads.@spawn), `Distributed.@spawnat` 및 `Distributed.@distributed`의 사용이 완료될 때까지 기다립니다. 포함된 비동기 작업에서 발생한 모든 예외는 수집되어 [`CompositeException`](@ref)으로 던져집니다.

# 예제

```julia-repl
julia> Threads.nthreads()
4

julia> @sync begin
           Threads.@spawn println("Thread-id $(Threads.threadid()), task 1")
           Threads.@spawn println("Thread-id $(Threads.threadid()), task 2")
       end;
Thread-id 3, task 1
Thread-id 1, task 2
```
