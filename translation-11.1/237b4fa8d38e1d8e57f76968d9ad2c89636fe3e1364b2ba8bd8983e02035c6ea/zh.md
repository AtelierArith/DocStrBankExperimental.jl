```
@sync
```

等待所有词法上封闭的 [`@async`](@ref)、[`@spawn`](@ref Threads.@spawn)、`Distributed.@spawnat` 和 `Distributed.@distributed` 的使用完成。所有由封闭的异步操作抛出的异常都会被收集并作为 [`CompositeException`](@ref) 抛出。

# 示例

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
