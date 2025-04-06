```
codeunit(s::AbstractString) -> Type{<:Union{UInt8, UInt16, UInt32}}
```

Devuelve el tipo de unidad de código del objeto de cadena dado. Para cadenas codificadas en ASCII, Latin-1 o UTF-8, esto sería `UInt8`; para UCS-2 y UTF-16 sería `UInt16`; para UTF-32 sería `UInt32`. El tipo de unidad de código no tiene que limitarse a estos tres tipos, pero es difícil pensar en codificaciones de cadena de uso general que no utilicen una de estas unidades. `codeunit(s)` es lo mismo que `typeof(codeunit(s,1))` cuando `s` es una cadena no vacía.

Ver también [`ncodeunits`](@ref).
