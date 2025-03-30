```
Task(func)
```

创建一个 `Task`（即协程）来执行给定的函数 `func`（该函数必须可以无参数调用）。当此函数返回时，任务将退出。任务将在构造时从父级的“世界年龄”中运行，当 [`schedule`](@ref)d。

!!! warning
    默认情况下，任务的粘性位将设置为 true `t.sticky`。这模拟了 [`@async`](@ref) 的历史默认值。粘性任务只能在它们首次调度的工作线程上运行，并且在调度时将使它们从中调度的任务变为粘性。要获得 [`Threads.@spawn`](@ref) 的行为，请手动将粘性位设置为 `false`。


# 示例

```jldoctest
julia> a() = sum(i for i in 1:1000);

julia> b = Task(a);
```

在这个例子中，`b` 是一个可运行的 `Task`，但尚未开始。
