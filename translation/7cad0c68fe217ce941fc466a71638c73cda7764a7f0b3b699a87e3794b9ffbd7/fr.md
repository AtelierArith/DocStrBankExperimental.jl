```
keytype(type)
```

Obtenez le type de clé d'un type de dictionnaire. Se comporte de manière similaire à [`eltype`](@ref).

# Exemples

```jldoctest
julia> keytype(Dict(Int32(1) => "foo"))
Int32
```
