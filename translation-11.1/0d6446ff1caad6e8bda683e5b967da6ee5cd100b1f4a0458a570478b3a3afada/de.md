```
getipaddr() -> IPAddr
```

Holen Sie sich eine IP-Adresse des lokalen Rechners, wobei IPv4 gegenüber IPv6 bevorzugt wird. Wirft eine Ausnahme, wenn keine Adressen verfügbar sind.

```
getipaddr(addr_type::Type{T}) where T<:IPAddr -> T
```

Holen Sie sich eine IP-Adresse des lokalen Rechners des angegebenen Typs. Wirft eine Ausnahme, wenn keine Adressen des angegebenen Typs verfügbar sind.

Diese Funktion ist ein Rückwärtskompatibilitäts-Wrapper um [`getipaddrs`](@ref). Neue Anwendungen sollten stattdessen [`getipaddrs`](@ref) verwenden.

# Beispiele

```julia-repl
julia> getipaddr()
ip"192.168.1.28"

julia> getipaddr(IPv6)
ip"fe80::9731:35af:e1c5:6e49"
```

Siehe auch [`getipaddrs`](@ref).
