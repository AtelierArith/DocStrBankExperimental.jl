```
manage(manager::ClusterManager, id::Integer, config::WorkerConfig. op::Symbol)
```

클러스터 관리자에 의해 구현됩니다. 작업자의 생애 동안 마스터 프로세스에서 호출되며, 적절한 `op` 값과 함께 호출됩니다:

  * 작업자가 Julia 작업자 풀에 추가/제거될 때 `:register`/`:deregister`와 함께.
  * `interrupt(workers)`가 호출될 때 `:interrupt`와 함께. `ClusterManager`는 적절한 작업자에게 인터럽트 신호를 보내야 합니다.
  * 정리 목적으로 `:finalize`와 함께.
