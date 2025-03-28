```
isvalid(T, value) -> Bool
```

Retourne `true` si la valeur donnée est valide pour ce type. Les types peuvent actuellement être soit `AbstractChar` soit `String`. Les valeurs pour `AbstractChar` peuvent être de type `AbstractChar` ou [`UInt32`](@ref). Les valeurs pour `String` peuvent être de ce type, `SubString{String}`, `Vector{UInt8}`, ou un sous-tableau contigu de celui-ci.

# Exemples

```jldoctest
julia> isvalid(Char, 0xd800)
false

julia> isvalid(String, SubString("thisisvalid",1,5))
true

julia> isvalid(Char, 0xd799)
true
```

!!! compat "Julia 1.6"
    Le support pour les valeurs de sous-tableau a été ajouté dans Julia 1.6.

