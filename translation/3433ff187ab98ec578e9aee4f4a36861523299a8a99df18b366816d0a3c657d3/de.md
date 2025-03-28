```
put!(rr::RemoteChannel, args...)
```

Speichern Sie eine Menge von Werten im [`RemoteChannel`](@ref). Wenn der Kanal voll ist, blockiert er, bis Platz verfügbar ist. Gibt das erste Argument zurück.
