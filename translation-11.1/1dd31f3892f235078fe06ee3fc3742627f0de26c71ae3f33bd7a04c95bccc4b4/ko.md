```
worker_id_from_socket(s) -> pid
```

주어진 `IO` 연결 또는 `Worker`에 대해 연결된 작업자의 `pid`를 반환하는 저수준 API입니다. 이는 수신 프로세스 ID에 따라 작성되는 데이터를 최적화하는 유형에 대한 사용자 정의 [`serialize`](@ref) 메서드를 작성할 때 유용합니다.
