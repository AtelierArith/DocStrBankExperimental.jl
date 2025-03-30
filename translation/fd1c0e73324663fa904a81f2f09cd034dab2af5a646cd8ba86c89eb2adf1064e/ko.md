```
addprocs(manager::ClusterManager; kwargs...) -> 프로세스 식별자 목록
```

지정된 클러스터 관리자를 통해 작업자 프로세스를 시작합니다.

예를 들어, Beowulf 클러스터는 패키지 `ClusterManagers.jl`에 구현된 사용자 정의 클러스터 관리자를 통해 지원됩니다.

새로 시작된 작업자가 마스터로부터 연결 설정을 기다리는 초 수는 작업자 프로세스의 환경에서 변수 `JULIA_WORKER_TIMEOUT`을 통해 지정할 수 있습니다. TCP/IP를 전송 수단으로 사용할 때만 관련이 있습니다.

REPL을 차단하지 않고 작업자를 시작하거나, 프로그래밍 방식으로 작업자를 시작하는 경우 포함된 함수에서 `addprocs`를 자체 작업으로 실행합니다.

# 예제

```julia
# 바쁜 클러스터에서 비동기적으로 `addprocs` 호출
t = @async addprocs(...)
```

```julia
# 작업자가 온라인 상태가 될 때마다 활용
if nprocs() > 1   # 최소한 하나의 새로운 작업자가 사용 가능해야 함
   ....   # 분산 실행 수행
end
```

```julia
# 새로 시작된 작업자 ID 또는 오류 메시지 검색
if istaskdone(t)   # `addprocs`가 완료되었는지 확인하여 `fetch`가 차단되지 않도록 함
    if nworkers() == N
        new_pids = fetch(t)
    else
        fetch(t)
    end
end
```
