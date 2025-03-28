```
keytype(type)
```

Erhalte den Schlüsseltyp eines Dictionary-Typs. Verhält sich ähnlich wie [`eltype`](@ref).

# Beispiele

```jldoctest
julia> keytype(Dict(Int32(1) => "foo"))
Int32
```
