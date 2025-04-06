```
closewrite(stream)
```

关闭全双工 I/O 流的写入部分。首先执行 [`flush`](@ref)。通知另一端不再向底层文件写入数据。这并不是所有 I/O 类型都支持的。

如果实现了 `closewrite`，则后续的 `read` 或 `eof` 调用如果会阻塞，则会抛出 EOF 或分别返回 true。如果流已经关闭，这个操作是幂等的。

# 示例

```jldoctest
julia> io = Base.BufferStream(); # 这永远不会阻塞，因此我们可以在同一个任务上进行读写

julia> write(io, "request");

julia> # 在这里调用 `read(io)` 会永远阻塞

julia> closewrite(io);

julia> read(io, String)
"request"
```
