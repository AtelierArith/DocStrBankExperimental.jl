```
IPv6(host::Integer) -> IPv6
```

Gibt ein IPv6-Objekt von der IP-Adresse `host` zurück, die als [`Integer`](@ref) formatiert ist.

# Beispiele

```jldoctest
julia> IPv6(3223256218)
ip"::c01e:fc9a"
```
