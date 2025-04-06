```
bind(chnl::Channel, task::Task)
```

将 `chnl` 的生命周期与一个任务关联。当任务终止时，`Channel` `chnl` 会自动关闭。任务中未捕获的任何异常会传播给所有在 `chnl` 上等待的任务。

`chnl` 对象可以在任务终止时显式关闭。终止的任务对已经关闭的 `Channel` 对象没有影响。

当一个通道绑定到多个任务时，第一个终止的任务将关闭该通道。当多个通道绑定到同一个任务时，任务的终止将关闭所有绑定的通道。

# 示例

```jldoctest
julia> c = Channel(0);

julia> task = @async foreach(i->put!(c, i), 1:4);

julia> bind(c,task);

julia> for i in c
           @show i
       end;
i = 1
i = 2
i = 3
i = 4

julia> isopen(c)
false
```

```jldoctest
julia> c = Channel(0);

julia> task = @async (put!(c, 1); error("foo"));

julia> bind(c, task);

julia> take!(c)
1

julia> put!(c, 1);
ERROR: TaskFailedException
Stacktrace:
[...]
    nested task error: foo
[...]
```
