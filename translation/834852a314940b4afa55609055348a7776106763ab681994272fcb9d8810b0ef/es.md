```
bind(socket::Union{TCPServer, UDPSocket, TCPSocket}, host::IPAddr, port::Integer; ipv6only=false, reuseaddr=false, kws...)
```

Vincula `socket` al `host:port` dado. Ten en cuenta que `0.0.0.0` escuchará en todos los dispositivos.

  * El parámetro `ipv6only` desactiva el modo de pila dual. Si `ipv6only=true`, solo se crea una pila IPv6.
  * Si `reuseaddr=true`, múltiples hilos o procesos pueden vincularse a la misma dirección sin error si todos establecen `reuseaddr=true`, pero solo el último en vincularse recibirá tráfico.
