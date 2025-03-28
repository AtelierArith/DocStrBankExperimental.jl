```
getalladdrinfo(host::AbstractString) -> Vector{IPAddr}
```

Erhält alle IP-Adressen des `host`. Verwendet die zugrunde liegende `getaddrinfo`-Implementierung des Betriebssystems, die möglicherweise eine DNS-Abfrage durchführt.

# Beispiele

```julia-repl
julia> getalladdrinfo("google.com")
2-element Array{IPAddr,1}:
 ip"172.217.6.174"
 ip"2607:f8b0:4000:804::200e"
```
