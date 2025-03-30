```
base64encode(writefunc, args...; context=nothing)
base64encode(args...; context=nothing)
```

给定一个类似于 [`write`](@ref) 的函数 `writefunc`，它将 I/O 流作为第一个参数，`base64encode(writefunc, args...)` 调用 `writefunc` 将 `args...` 写入一个 base64 编码的字符串，并返回该字符串。`base64encode(args...)` 等价于 `base64encode(write, args...)`：它使用标准的 [`write`](@ref) 函数将其参数转换为字节，并返回 base64 编码的字符串。

可选的关键字参数 `context` 可以设置为 `:key=>value` 对或一个 `IO` 或 [`IOContext`](@ref) 对象，其属性用于传递给 `writefunc` 或 `write` 的 I/O 流。

另请参见 [`base64decode`](@ref)。
