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

Diese Schnittstelle bietet einen Mechanismus zum Starten und Verwalten von Julia-Arbeitern in verschiedenen Cluster-Umgebungen. Es gibt zwei Arten von Managern in Base: `LocalManager`, um zusätzliche Arbeiter auf demselben Host zu starten, und `SSHManager`, um auf entfernten Hosts über `ssh` zu starten. TCP/IP-Sockets werden verwendet, um Prozesse zu verbinden und Nachrichten zwischen ihnen zu transportieren. Es ist möglich, dass Cluster-Manager einen anderen Transport bereitstellen.

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
