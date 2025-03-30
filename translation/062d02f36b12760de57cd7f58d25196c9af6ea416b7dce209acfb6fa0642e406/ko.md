```
kill(manager::ClusterManager, pid::Int, config::WorkerConfig)
```

클러스터 관리자에 의해 구현됩니다. 이는 마스터 프로세스에서 [`rmprocs`](@ref)에 의해 호출됩니다. 이는 `pid`로 지정된 원격 작업자가 종료되도록 해야 합니다. `kill(manager::ClusterManager.....)`는 `pid`에서 원격 `exit()`를 실행합니다.
