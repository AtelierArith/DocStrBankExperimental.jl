```
listenany([host::IPAddr,] port_hint; backlog::Integer=BACKLOG_DEFAULT) -> (UInt16, TCPServer)
```

Crea un `TCPServer` en cualquier puerto, utilizando hint como punto de partida. Devuelve una tupla del puerto real en el que se creó el servidor y el servidor mismo. El argumento backlog define la longitud máxima a la que puede crecer la cola de conexiones pendientes para sockfd.
