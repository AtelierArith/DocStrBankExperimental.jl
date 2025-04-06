```
@task
```

将一个表达式包装在一个 [`Task`](@ref) 中而不执行它，并返回该 [`Task`](@ref)。这仅仅创建一个任务，而不运行它。

!!! warning
    默认情况下，任务的粘性位将被设置为 true `t.sticky`。这模拟了 [`@async`](@ref) 的历史默认值。粘性任务只能在它们首次调度的工作线程上运行，并且在调度时会使它们从中调度的任务变为粘性。要获得 [`Threads.@spawn`](@ref) 的行为，请手动将粘性位设置为 `false`。


# 示例

```jldoctest
julia> a1() = sum(i for i in 1:1000);

julia> b = @task a1();

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskdone(b)
true
```
