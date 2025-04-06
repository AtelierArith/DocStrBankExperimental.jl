```
valtype(type)
```

Erhalte den Werttyp eines Dictionary-Typs. Verhält sich ähnlich wie [`eltype`](@ref).

# Beispiele

```jldoctest
julia> valtype(Dict(Int32(1) => "foo"))
String
```
