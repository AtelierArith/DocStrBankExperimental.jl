```
schedule(t::Task, [val]; error=false)
```

将一个 [`Task`](@ref) 添加到调度器的队列中。这会导致任务在系统其他空闲时不断运行，除非该任务执行了阻塞操作，例如 [`wait`](@ref)。

如果提供了第二个参数 `val`，它将在任务再次运行时通过 [`yieldto`](@ref) 的返回值传递给任务。如果 `error` 为 `true`，则该值将在被唤醒的任务中作为异常抛出。

!!! warning
    在已经启动的任意 `Task` 上使用 `schedule` 是不正确的。有关更多信息，请参见 [API 参考](@ref low-level-schedule-wait)。


!!! warning
    默认情况下，任务的粘性位将设置为 true `t.sticky`。这模拟了 [`@async`](@ref) 的历史默认值。粘性任务只能在它们首次调度的工作线程上运行，并且在调度时会使它们被调度的任务变为粘性。要获得 [`Threads.@spawn`](@ref) 的行为，请手动将粘性位设置为 `false`。


# 示例

```jldoctest
julia> a5() = sum(i for i in 1:1000);

julia> b = Task(a5);

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskstarted(b)
true

julia> istaskdone(b)
true
```
