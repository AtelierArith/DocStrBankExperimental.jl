```
Threads.@spawn [:default|:interactive] expr
```

创建一个 [`Task`](@ref) 并将其 [`schedule`](@ref) 到指定线程池中的任何可用线程（如果未指定，则为 `:default`）。一旦有线程可用，任务就会被分配到该线程。要等待任务完成，请在此宏的结果上调用 [`wait`](@ref)，或调用 [`fetch`](@ref) 以等待并获取其返回值。

可以通过 `$` 将值插入到 `@spawn` 中，这会将值直接复制到构造的底层闭包中。这允许您插入变量的 *值*，将异步代码与当前任务中变量值的变化隔离开来。

!!! note
    任务运行的线程可能会在任务让出时改变，因此 `threadid()` 不应被视为任务的常量。请参见 [`Task Migration`](@ref man-task-migration)，以及更广泛的 [multi-threading](@ref man-multithreading) 手册以获取更多重要注意事项。另请参见关于 [threadpools](@ref man-threadpools) 的章节。


!!! compat "Julia 1.3"
    此宏自 Julia 1.3 起可用。


!!! compat "Julia 1.4"
    自 Julia 1.4 起可通过 `$` 插入值。


!!! compat "Julia 1.9"
    自 Julia 1.9 起可以指定线程池。


# 示例

```julia-repl
julia> t() = println("Hello from ", Threads.threadid());

julia> tasks = fetch.([Threads.@spawn t() for i in 1:4]);
Hello from 1
Hello from 1
Hello from 3
Hello from 4
```
