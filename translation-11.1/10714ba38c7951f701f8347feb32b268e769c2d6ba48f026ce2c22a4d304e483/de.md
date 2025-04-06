```
isvalid(T, value) -> Bool
```

Gibt `true` zurück, wenn der angegebene Wert für diesen Typ gültig ist. Typen können derzeit entweder `AbstractChar` oder `String` sein. Werte für `AbstractChar` können vom Typ `AbstractChar` oder [`UInt32`](@ref) sein. Werte für `String` können von diesem Typ, `SubString{String}`, `Vector{UInt8}` oder einem zusammenhängenden Teilarray davon sein.

# Beispiele

```jldoctest
julia> isvalid(Char, 0xd800)
false

julia> isvalid(String, SubString("thisisvalid",1,5))
true

julia> isvalid(Char, 0xd799)
true
```

!!! compat "Julia 1.6"
    Unterstützung für Teilarray-Werte wurde in Julia 1.6 hinzugefügt.

