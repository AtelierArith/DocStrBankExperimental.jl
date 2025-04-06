```
elsize(type)
```

Calcule le pas mémoire en octets entre les éléments consécutifs de [`eltype`](@ref) stockés à l'intérieur du `type` donné, si les éléments du tableau sont stockés de manière dense avec un pas linéaire uniforme.

# Exemples

```jldoctest
julia> Base.elsize(rand(Float32, 10))
4
```
