```
take!(c::Channel)
```

从 [`Channel`](@ref) 中按顺序移除并返回一个值。阻塞直到数据可用。对于无缓冲通道，阻塞直到其他任务执行 [`put!`](@ref)。

# 示例

缓冲通道：

```jldoctest
julia> c = Channel(1);

julia> put!(c, 1);

julia> take!(c)
1
```

无缓冲通道：

```jldoctest
julia> c = Channel(0);

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);

julia> take!(c)
1
```
