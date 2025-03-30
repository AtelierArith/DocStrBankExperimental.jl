```
Threads.foreach(f, channel::Channel;
                schedule::Threads.AbstractSchedule=Threads.FairSchedule(),
                ntasks=Threads.threadpoolsize())
```

类似于 `foreach(f, channel)`，但对 `channel` 的迭代和对 `f` 的调用是在 `Threads.@spawn` 生成的 `ntasks` 任务之间分配的。此函数将在所有内部生成的任务完成之前等待返回。

如果 `schedule isa FairSchedule`，`Threads.foreach` 将尝试以一种方式生成任务，使得 Julia 的调度器能够更自由地在线程之间负载平衡工作项。这种方法通常具有更高的每项开销，但在与其他多线程工作负载并发时可能表现得比 `StaticSchedule` 更好。

如果 `schedule isa StaticSchedule`，`Threads.foreach` 将以一种产生比 `FairSchedule` 更低的每项开销的方式生成任务，但不太适合负载平衡。因此，这种方法可能更适合细粒度、均匀的工作负载，但在与其他多线程工作负载并发时可能表现得比 `FairSchedule` 更差。

# 示例

```julia-repl
julia> n = 20

julia> c = Channel{Int}(ch -> foreach(i -> put!(ch, i), 1:n), 1)

julia> d = Channel{Int}(n) do ch
           f = i -> put!(ch, i^2)
           Threads.foreach(f, c)
       end

julia> collect(d)
collect(d) = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

!!! compat "Julia 1.6"
    此函数需要 Julia 1.6 或更高版本。

