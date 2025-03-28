```
getipaddrs(addr_type::Type{T}=IPAddr; loopback::Bool=false) where T<:IPAddr -> Vector{T}
```

Obtiene las direcciones IP de la máquina local.

Configurar el parámetro opcional `addr_type` a `IPv4` o `IPv6` hace que solo se devuelvan direcciones de ese tipo.

El argumento clave `loopback` determina si se incluyen las direcciones de loopback (por ejemplo, `ip"127.0.0.1"`, `ip"::1"`).

!!! compat "Julia 1.2"
    Esta función está disponible a partir de Julia 1.2.


# Ejemplos

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

Ver también [`islinklocaladdr`](@ref).
