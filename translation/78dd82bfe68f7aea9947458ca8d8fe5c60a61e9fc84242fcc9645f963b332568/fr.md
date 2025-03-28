```
IPv6(hôte::Integer) -> IPv6
```

Retourne un objet IPv6 à partir de l'adresse IP `hôte` formatée comme un [`Integer`](@ref).

# Exemples

```jldoctest
julia> IPv6(3223256218)
ip"::c01e:fc9a"
```
