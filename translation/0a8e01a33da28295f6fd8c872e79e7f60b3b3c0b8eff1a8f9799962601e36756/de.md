```
TCPSocket(; delay=true)
```

Öffnen Sie einen TCP-Socket mit libuv. Wenn `delay` wahr ist, verzögert libuv die Erstellung des Dateideskriptors des Sockets bis zum ersten [`bind`](@ref) Aufruf. `TCPSocket` hat verschiedene Felder, um den Zustand des Sockets sowie seine Sende-/Empfangspuffer anzuzeigen.
