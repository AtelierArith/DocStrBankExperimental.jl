```
eof(stream) -> Bool
```

测试一个 I/O 流是否到达文件末尾。如果流尚未耗尽，则此函数将在必要时阻塞以等待更多数据，然后返回 `false`。因此，在看到 `eof` 返回 `false` 后，始终安全地读取一个字节。只要缓冲的数据仍然可用，即使连接的远程端已关闭，`eof` 也会返回 `false`。

# 示例

```jldoctest
julia> b = IOBuffer("my buffer");

julia> eof(b)
false

julia> seekend(b);

julia> eof(b)
true
```
