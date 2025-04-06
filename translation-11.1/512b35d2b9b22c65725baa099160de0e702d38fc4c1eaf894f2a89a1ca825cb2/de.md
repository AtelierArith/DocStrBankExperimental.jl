```
getaddrinfo(host::AbstractString, IPAddr) -> IPAddr
```

Erhält die erste IP-Adresse des `host` des angegebenen `IPAddr`-Typs. Verwendet die zugrunde liegende Implementierung von getaddrinfo des Betriebssystems, die möglicherweise eine DNS-Abfrage durchführt.

# Beispiele

```julia-repl
julia> getaddrinfo("localhost", IPv6)
ip"::1"

julia> getaddrinfo("localhost", IPv4)
ip"127.0.0.1"
```
