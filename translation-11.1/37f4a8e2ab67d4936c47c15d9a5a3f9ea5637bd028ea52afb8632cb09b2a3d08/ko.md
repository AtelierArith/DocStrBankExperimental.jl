```
launch(manager::ClusterManager, params::Dict, launched::Array, launch_ntfy::Condition)
```

클러스터 관리자에 의해 구현됩니다. 이 함수에 의해 시작된 모든 Julia 작업자에 대해 `launched`에 `WorkerConfig` 항목을 추가하고 `launch_ntfy`를 알립니다. 이 함수는 `manager`에 의해 요청된 모든 작업자가 시작되면 반드시 종료되어야 합니다. `params`는 [`addprocs`](@ref) 호출 시 사용된 모든 키워드 인수의 사전입니다.
