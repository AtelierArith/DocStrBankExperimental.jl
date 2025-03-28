```
isready(rr::Future)
```

Bestimmen Sie, ob ein [`Future`](@ref) einen Wert gespeichert hat.

Wenn das Argument `Future` von einem anderen Knoten besessen wird, wird dieser Aufruf blockieren, um auf die Antwort zu warten. Es wird empfohlen, auf `rr` in einer separaten Aufgabe zu warten oder einen lokalen [`Channel`](@ref) als Proxy zu verwenden:

```julia
p = 1
f = Future(p)
errormonitor(@async put!(f, remotecall_fetch(long_computation, p)))
isready(f)  # wird nicht blockieren
```
