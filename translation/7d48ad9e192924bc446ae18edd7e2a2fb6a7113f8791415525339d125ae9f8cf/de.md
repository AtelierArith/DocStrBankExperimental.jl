```
getipaddrs(addr_type::Type{T}=IPAddr; loopback::Bool=false) where T<:IPAddr -> Vector{T}
```

Holen Sie sich die IP-Adressen des lokalen Computers.

Wenn der optionale Parameter `addr_type` auf `IPv4` oder `IPv6` gesetzt wird, werden nur Adressen dieses Typs zurückgegeben.

Das Schlüsselwortargument `loopback` bestimmt, ob Loopback-Adressen (z. B. `ip"127.0.0.1"`, `ip"::1"`) einbezogen werden.

!!! compat "Julia 1.2"
    Diese Funktion ist seit Julia 1.2 verfügbar.


# Beispiele

```julia-repl
julia> getipaddrs()
5-element Array{IPAddr,1}:
 ip"198.51.100.17"
 ip"203.0.113.2"
 ip"2001:db8:8:4:445e:5fff:fe5d:5500"
 ip"2001:db8:8:4:c164:402e:7e3c:3668"
 ip"fe80::445e:5fff:fe5d:5500"

julia> getipaddrs(IPv6)
3-element Array{IPv6,1}:
 ip"2001:db8:8:4:445e:5fff:fe5d:5500"
 ip"2001:db8:8:4:c164:402e:7e3c:3668"
 ip"fe80::445e:5fff:fe5d:5500"
```

Siehe auch [`islinklocaladdr`](@ref).
