```
IPv4(host::Integer) -> IPv4
```

Devuelve un objeto IPv4 a partir de la dirección IP `host` formateada como un [`Integer`](@ref).

# Ejemplos

```jldoctest
julia> IPv4(3223256218)
ip"192.30.252.154"
```
