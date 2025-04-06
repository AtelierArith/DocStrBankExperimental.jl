```
valtype(type)
```

Obtenez le type de valeur d'un type de dictionnaire. Se comporte de manière similaire à [`eltype`](@ref).

# Exemples

```jldoctest
julia> valtype(Dict(Int32(1) => "foo"))
String
```
