```
TCPSocket(; delay=true)
```

Abre un socket TCP usando libuv. Si `delay` es verdadero, libuv retrasa la creación del descriptor de archivo del socket hasta la primera llamada a [`bind`](@ref). `TCPSocket` tiene varios campos para denotar el estado del socket, así como sus buffers de envío/recepción.
