```
isready(c::Channel)
```

确定一个 [`Channel`](@ref) 是否有值存储在其中。立即返回，不会阻塞。

对于无缓冲通道，如果有任务在等待 [`put!`](@ref)，则返回 `true`。

# 示例

缓冲通道：

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> put!(c, 1);

julia> isready(c)
true
```

无缓冲通道：

```jldoctest
julia> c = Channel();

julia> isready(c)  # 没有任务在等待放入！
false

julia> task = Task(() -> put!(c, 1));

julia> schedule(task);  # 安排一个 put! 任务

julia> isready(c)
true
```
