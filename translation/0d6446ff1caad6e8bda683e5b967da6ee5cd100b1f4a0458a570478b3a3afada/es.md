```
getipaddr() -> IPAddr
```

Obtiene una dirección IP de la máquina local, prefiriendo IPv4 sobre IPv6. Lanza una excepción si no hay direcciones disponibles.

```
getipaddr(addr_type::Type{T}) where T<:IPAddr -> T
```

Obtiene una dirección IP de la máquina local del tipo especificado. Lanza una excepción si no hay direcciones del tipo especificado disponibles.

Esta función es un envoltorio de compatibilidad hacia atrás alrededor de [`getipaddrs`](@ref). Las nuevas aplicaciones deben usar [`getipaddrs`](@ref) en su lugar.

# Ejemplos

```julia-repl
julia> getipaddr()
ip"192.168.1.28"

julia> getipaddr(IPv6)
ip"fe80::9731:35af:e1c5:6e49"
```

Ver también [`getipaddrs`](@ref).
