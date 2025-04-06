```
bind(socket::Union{TCPServer, UDPSocket, TCPSocket}, host::IPAddr, port::Integer; ipv6only=false, reuseaddr=false, kws...)
```

Liez `socket` à l'`hôte:port` donné. Notez que `0.0.0.0` écoutera sur tous les appareils.

  * Le paramètre `ipv6only` désactive le mode double pile. Si `ipv6only=true`, seule une pile IPv6 est créée.
  * Si `reuseaddr=true`, plusieurs threads ou processus peuvent se lier à la même adresse sans erreur s'ils définissent tous `reuseaddr=true`, mais seul le dernier à se lier recevra du trafic.
