```
connect(manager::ClusterManager, pid::Int, config::WorkerConfig) -> (instrm::IO, outstrm::IO)
```

由使用自定义传输的集群管理器实现。它应该建立与指定为 `config` 的 `pid` 的工作者的逻辑连接，并返回一对 `IO` 对象。从 `pid` 到当前进程的消息将从 `instrm` 中读取，而要发送到 `pid` 的消息将写入 `outstrm`。自定义传输实现必须确保消息被完整且按顺序传递和接收。`connect(manager::ClusterManager.....)` 在工作者之间设置 TCP/IP 套接字连接。
