```
Future(w::Int, rrid::RRID, v::Union{Some, Nothing}=nothing)
```

Ein `Future` ist ein Platzhalter für eine einzelne Berechnung mit unbekanntem Abschlussstatus und -zeit. Für mehrere potenzielle Berechnungen siehe `RemoteChannel`. Siehe `remoteref_id` zur Identifizierung eines `AbstractRemoteRef`.
