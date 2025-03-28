```
getipaddrs(addr_type::Type{T}=IPAddr; loopback::Bool=false) where T<:IPAddr -> Vector{T}
```

Obtenez les adresses IP de la machine locale.

Définir le paramètre optionnel `addr_type` sur `IPv4` ou `IPv6` entraîne le retour uniquement des adresses de ce type.

L'argument clé `loopback` détermine si les adresses de boucle (par exemple `ip"127.0.0.1"`, `ip"::1"`) sont incluses.

!!! compat "Julia 1.2"
    Cette fonction est disponible depuis Julia 1.2.


# Exemples

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

Voir aussi [`islinklocaladdr`](@ref).
