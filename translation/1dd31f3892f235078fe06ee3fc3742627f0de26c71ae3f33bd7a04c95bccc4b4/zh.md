```
worker_id_from_socket(s) -> pid
```

一个低级 API，给定一个 `IO` 连接或一个 `Worker`，返回它所连接的工作者的 `pid`。在为一个类型编写自定义 [`serialize`](@ref) 方法时，这非常有用，因为它根据接收进程的 id 优化写出的数据。
