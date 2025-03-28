```
codeunit(s::AbstractString) -> Type{<:Union{UInt8, UInt16, UInt32}}
```

Renvoie le type d'unité de code de l'objet chaîne donné. Pour les chaînes encodées en ASCII, Latin-1 ou UTF-8, cela serait `UInt8` ; pour UCS-2 et UTF-16, cela serait `UInt16` ; pour UTF-32, cela serait `UInt32`. Le type d'unité de code ne doit pas être limité à ces trois types, mais il est difficile de penser à des encodages de chaînes largement utilisés qui n'utilisent pas l'une de ces unités. `codeunit(s)` est le même que `typeof(codeunit(s,1))` lorsque `s` est une chaîne non vide.

Voir aussi [`ncodeunits`](@ref).
