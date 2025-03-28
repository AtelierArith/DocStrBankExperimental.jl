```
nagle(socket::Union{TCPServer, TCPSocket}, enable::Bool)
```

Nagels Algorithmus bündelt mehrere kleine TCP-Pakete zu größeren. Dies kann den Durchsatz verbessern, aber die Latenz verschlechtern. Nagels Algorithmus ist standardmäßig aktiviert. Diese Funktion legt fest, ob Nagels Algorithmus auf einem bestimmten TCP-Server oder Socket aktiv ist. Die entgegengesetzte Option wird in anderen Sprachen `TCP_NODELAY` genannt.

!!! compat "Julia 1.3"
    Diese Funktion erfordert Julia 1.3 oder höher.

