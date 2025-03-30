```
stringmime(mime, x; context=nothing)
```

返回一个 `AbstractString`，包含以请求的 `mime` 类型表示的 `x`。这类似于 [`repr(mime, x)`](@ref)，但二进制数据以 ASCII 字符串的形式进行 base64 编码。

可选的关键字参数 `context` 可以设置为 `:key=>value` 对或一个 `IO` 或 [`IOContext`](@ref) 对象，其属性用于传递给 [`show`](@ref) 的 I/O 流。
