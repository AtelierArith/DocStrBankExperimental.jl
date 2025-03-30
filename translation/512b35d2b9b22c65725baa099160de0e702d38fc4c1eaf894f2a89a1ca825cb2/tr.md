```
getaddrinfo(host::AbstractString, IPAddr) -> IPAddr
```

Belirtilen `IPAddr` türündeki `host`'un ilk IP adresini alır. İşletim sisteminin temel getaddrinfo uygulamasını kullanır, bu da bir DNS sorgusu yapabilir.

# Örnekler

```julia-repl
julia> getaddrinfo("localhost", IPv6)
ip"::1"

julia> getaddrinfo("localhost", IPv4)
ip"127.0.0.1"
```
