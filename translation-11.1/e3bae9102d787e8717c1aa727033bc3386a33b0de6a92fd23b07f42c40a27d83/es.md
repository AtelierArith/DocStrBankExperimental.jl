```
Future(w::Int, rrid::RRID, v::Union{Some, Nothing}=nothing)
```

Un `Future` es un marcador de posición para un solo cálculo de estado de terminación y tiempo desconocidos. Para múltiples cálculos potenciales, consulte `RemoteChannel`. Consulte `remoteref_id` para identificar un `AbstractRemoteRef`.
