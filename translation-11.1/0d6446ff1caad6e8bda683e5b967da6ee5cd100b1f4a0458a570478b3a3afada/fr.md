```
getipaddr() -> IPAddr
```

Obtenez une adresse IP de la machine locale, en préférant IPv4 à IPv6. Lève une exception si aucune adresse n'est disponible.

```
getipaddr(addr_type::Type{T}) where T<:IPAddr -> T
```

Obtenez une adresse IP de la machine locale du type spécifié. Lève une exception si aucune adresse du type spécifié n'est disponible.

Cette fonction est un wrapper de compatibilité ascendante autour de [`getipaddrs`](@ref). Les nouvelles applications devraient utiliser [`getipaddrs`](@ref) à la place.

# Exemples

```julia-repl
julia> getipaddr()
ip"192.168.1.28"

julia> getipaddr(IPv6)
ip"fe80::9731:35af:e1c5:6e49"
```

Voir aussi [`getipaddrs`](@ref).
