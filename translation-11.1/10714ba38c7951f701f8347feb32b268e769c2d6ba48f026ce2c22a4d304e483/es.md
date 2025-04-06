```
isvalid(T, value) -> Bool
```

Devuelve `true` si el valor dado es válido para ese tipo. Los tipos actualmente pueden ser `AbstractChar` o `String`. Los valores para `AbstractChar` pueden ser de tipo `AbstractChar` o [`UInt32`](@ref). Los valores para `String` pueden ser de ese tipo, `SubString{String}`, `Vector{UInt8}`, o un subarreglo contiguo de estos.

# Ejemplos

```jldoctest
julia> isvalid(Char, 0xd800)
false

julia> isvalid(String, SubString("thisisvalid",1,5))
true

julia> isvalid(Char, 0xd799)
true
```

!!! compat "Julia 1.6"
    El soporte para valores de subarreglo se agregó en Julia 1.6.

