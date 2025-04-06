```
wait(c::Channel)
```

阻塞直到 `Channel` [`isready`](@ref)。

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> task = Task(() -> wait(c));

julia> schedule(task);

julia> istaskdone(task)  # 任务被阻塞，因为通道未准备好
false

julia> put!(c, 1);

julia> istaskdone(task)  # 任务现在已解除阻塞
true
```
