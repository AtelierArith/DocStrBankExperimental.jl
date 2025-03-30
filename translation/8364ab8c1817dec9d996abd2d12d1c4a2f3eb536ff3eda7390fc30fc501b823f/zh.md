```
fdio([name::AbstractString, ]fd::Integer[, own::Bool=false]) -> IOStream
```

从整数文件描述符创建一个[`IOStream`](@ref)对象。如果`own`为`true`，关闭此对象将关闭底层描述符。默认情况下，当`IOStream`被垃圾回收时会被关闭。`name`允许您将描述符与命名文件关联。
