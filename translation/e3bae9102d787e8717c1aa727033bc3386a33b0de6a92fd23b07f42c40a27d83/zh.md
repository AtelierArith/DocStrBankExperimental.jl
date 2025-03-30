```
Future(w::Int, rrid::RRID, v::Union{Some, Nothing}=nothing)
```

`Future` 是一个占位符，用于表示一个未知终止状态和时间的单一计算。有关多个潜在计算的信息，请参见 `RemoteChannel`。有关识别 `AbstractRemoteRef` 的信息，请参见 `remoteref_id`。
