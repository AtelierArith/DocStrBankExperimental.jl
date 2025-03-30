```
Future(w::Int, rrid::RRID, v::Union{Some, Nothing}=nothing)
```

`Future`는 알 수 없는 종료 상태와 시간을 가진 단일 계산을 위한 자리 표시자입니다. 여러 잠재적 계산에 대해서는 `RemoteChannel`을 참조하십시오. `AbstractRemoteRef`를 식별하기 위해 `remoteref_id`를 참조하십시오.
