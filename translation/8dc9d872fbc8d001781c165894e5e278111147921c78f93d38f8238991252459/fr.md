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

Cette interface fournit un mécanisme pour lancer et gérer des travailleurs Julia sur différents environnements de cluster. Il existe deux types de gestionnaires présents dans Base : `LocalManager`, pour lancer des travailleurs supplémentaires sur le même hôte, et `SSHManager`, pour lancer sur des hôtes distants via `ssh`. Des sockets TCP/IP sont utilisés pour se connecter et transporter des messages entre les processus. Il est possible que les gestionnaires de cluster fournissent un transport différent.

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
