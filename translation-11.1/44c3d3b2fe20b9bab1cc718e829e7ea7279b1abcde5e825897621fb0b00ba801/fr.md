```
nagle(socket::Union{TCPServer, TCPSocket}, enable::Bool)
```

L'algorithme de Nagle regroupe plusieurs petits paquets TCP en paquets plus grands. Cela peut améliorer le débit mais aggraver la latence. L'algorithme de Nagle est activé par défaut. Cette fonction définit si l'algorithme de Nagle est actif sur un serveur TCP ou un socket donné. L'option opposée est appelée `TCP_NODELAY` dans d'autres langages.

!!! compat "Julia 1.3"
    Cette fonction nécessite Julia 1.3 ou une version ultérieure.

