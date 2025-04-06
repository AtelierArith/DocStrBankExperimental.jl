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

Bu arayüz, farklı küme ortamlarında Julia işçilerini başlatmak ve yönetmek için bir mekanizma sağlar. Temel içinde iki tür yönetici bulunmaktadır: `LocalManager`, aynı ana makinede ek işçiler başlatmak için ve `SSHManager`, uzaktaki ana makinelerde `ssh` aracılığıyla başlatmak için. İşlemler arasında bağlantı kurmak ve mesajları taşımak için TCP/IP soketleri kullanılır. Küme Yöneticilerinin farklı bir taşıma sağlaması mümkündür.

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
