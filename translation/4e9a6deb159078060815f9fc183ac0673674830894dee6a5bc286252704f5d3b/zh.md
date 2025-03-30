```
WorkerConfig
```

由 [`ClusterManager`](@ref) 使用的类型，用于控制添加到其集群中的工作者。一些字段被所有集群管理器用于访问主机：

  * `io` – 用于访问工作者的连接（`IO` 的子类型或 `Nothing`）
  * `host` – 主机地址（可以是 `String` 或 `Nothing`）
  * `port` – 用于连接工作者的主机端口（可以是 `Int` 或 `Nothing`）

一些字段被集群管理器用于向已初始化的主机添加工作者：

  * `count` – 要在主机上启动的工作者数量
  * `exename` – 主机上 Julia 可执行文件的路径，默认为 `"$(Sys.BINDIR)/julia"` 或 `"$(Sys.BINDIR)/julia-debug"`
  * `exeflags` – 启动远程 Julia 时使用的标志

`userdata` 字段用于外部管理器存储每个工作者的信息。

一些字段被 `SSHManager` 和类似的管理器使用：

  * `tunnel` – `true`（使用隧道），`false`（不使用隧道），或 [`nothing`](@ref)（使用管理器的默认设置）
  * `multiplex` – `true`（使用 SSH 复用进行隧道）或 `false`
  * `forward` – 用于 ssh 的 `-L` 选项的转发选项
  * `bind_addr` – 在远程主机上绑定的地址
  * `sshflags` – 用于建立 SSH 连接的标志
  * `max_parallel` – 在主机上并行连接的最大工作者数量

一些字段被 `LocalManager` 和 `SSHManager` 都使用：

  * `connect_at` – 确定这是工作者到工作者还是驱动程序到工作者的设置调用
  * `process` – 将要连接的进程（通常管理器会在 [`addprocs`](@ref) 期间分配此项）
  * `ospid` – 根据主机操作系统的进程 ID，用于中断工作者进程
  * `environ` – 本地/SSH 管理器用于存储临时信息的私有字典
  * `ident` – 由 [`ClusterManager`](@ref) 识别的工作者
  * `connect_idents` – 如果使用自定义拓扑，工作者必须连接的工作者 ID 列表
  * `enable_threaded_blas` – `true`、`false` 或 `nothing`，是否在工作者上使用线程化 BLAS
