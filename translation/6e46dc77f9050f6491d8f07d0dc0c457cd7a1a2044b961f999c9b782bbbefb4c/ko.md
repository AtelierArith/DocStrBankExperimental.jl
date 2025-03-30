```
init_worker(cookie::AbstractString, manager::ClusterManager=DefaultClusterManager())
```

사용자 정의 전송을 구현하는 클러스터 관리자가 호출합니다. 새로 시작된 프로세스를 작업자로 초기화합니다. 명령줄 인수 `--worker[=<cookie>]`는 TCP/IP 소켓을 사용하여 프로세스를 작업자로 초기화하는 효과가 있습니다. `cookie`는 [`cluster_cookie`](@ref)입니다.
