# [Distributed Computing](@id man-distributed)

```@docs
Distributed
Distributed.addprocs
Distributed.nprocs
Distributed.nworkers
Distributed.procs()
Distributed.procs(::Integer)
Distributed.workers
Distributed.rmprocs
Distributed.interrupt
Distributed.myid
Distributed.pmap
Distributed.RemoteException
Distributed.ProcessExitedException
Distributed.Future
Distributed.RemoteChannel
Distributed.fetch(::Distributed.Future)
Distributed.fetch(::RemoteChannel)
Distributed.remotecall(::Any, ::Integer, ::Any...)
Distributed.remotecall_wait(::Any, ::Integer, ::Any...)
Distributed.remotecall_fetch(::Any, ::Integer, ::Any...)
Distributed.remote_do(::Any, ::Integer, ::Any...)
Distributed.put!(::RemoteChannel, ::Any...)
Distributed.put!(::Distributed.Future, ::Any)
Distributed.take!(::RemoteChannel, ::Any...)
Distributed.isready(::RemoteChannel, ::Any...)
Distributed.isready(::Distributed.Future)
Distributed.AbstractWorkerPool
Distributed.WorkerPool
Distributed.CachingPool
Distributed.default_worker_pool
Distributed.clear!
Distributed.remote
Distributed.remotecall(::Any, ::AbstractWorkerPool, ::Any...)
Distributed.remotecall_wait(::Any, ::AbstractWorkerPool, ::Any...)
Distributed.remotecall_fetch(::Any, ::AbstractWorkerPool, ::Any...)
Distributed.remote_do(::Any, ::AbstractWorkerPool, ::Any...)
Distributed.@spawn
Distributed.@spawnat
Distributed.@fetch
Distributed.@fetchfrom
Distributed.@distributed
Distributed.@everywhere
Distributed.remoteref_id
Distributed.channel_from_id
Distributed.worker_id_from_socket
Distributed.cluster_cookie()
Distributed.cluster_cookie(::Any)
```

## Cluster Manager Interface

此接口提供了一种机制，用于在不同的集群环境中启动和管理 Julia 工作进程。Base 中存在两种类型的管理器：`LocalManager`，用于在同一主机上启动额外的工作进程，以及 `SSHManager`，用于通过 `ssh` 在远程主机上启动工作进程。TCP/IP 套接字用于连接和传输进程之间的消息。集群管理器可以提供不同的传输方式。

```@docs
Distributed.ClusterManager
Distributed.WorkerConfig
Distributed.launch
Distributed.manage
Distributed.kill(::ClusterManager, ::Int, ::WorkerConfig)
Distributed.connect(::ClusterManager, ::Int, ::WorkerConfig)
Distributed.init_worker
Distributed.start_worker
Distributed.process_messages
Distributed.default_addprocs_params
```
