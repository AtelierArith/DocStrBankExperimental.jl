```
Future(w::Int, rrid::RRID, v::Union{Some, Nothing}=nothing)
```

Un `Future` est un espace réservé pour un calcul unique dont le statut de terminaison et le temps sont inconnus. Pour plusieurs calculs potentiels, voir `RemoteChannel`. Voir `remoteref_id` pour identifier un `AbstractRemoteRef`.
