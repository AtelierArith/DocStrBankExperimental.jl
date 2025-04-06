```
IPv6(host::Integer) -> IPv6
```

Devuelve un objeto IPv6 a partir de la dirección IP `host` formateada como un [`Integer`](@ref).

# Ejemplos

```jldoctest
julia> IPv6(3223256218)
ip"::c01e:fc9a"
```
