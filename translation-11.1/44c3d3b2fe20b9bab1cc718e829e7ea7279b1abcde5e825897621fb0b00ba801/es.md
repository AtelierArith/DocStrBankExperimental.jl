```
nagle(socket::Union{TCPServer, TCPSocket}, enable::Bool)
```

El algoritmo de Nagle agrupa múltiples paquetes TCP pequeños en paquetes más grandes. Esto puede mejorar el rendimiento pero empeorar la latencia. El algoritmo de Nagle está habilitado por defecto. Esta función establece si el algoritmo de Nagle está activo en un servidor TCP o socket dado. La opción opuesta se llama `TCP_NODELAY` en otros lenguajes.

!!! compat "Julia 1.3"
    Esta función requiere Julia 1.3 o posterior.

