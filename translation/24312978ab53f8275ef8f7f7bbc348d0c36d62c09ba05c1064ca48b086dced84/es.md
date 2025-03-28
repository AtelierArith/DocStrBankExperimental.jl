```
islowercase(c::AbstractChar) -> Bool
```

Prueba si un carácter es una letra minúscula (de acuerdo con la propiedad derivada `Lowercase` del estándar Unicode).

Véase también [`isuppercase`](@ref).

# Ejemplos

```jldoctest
julia> islowercase('α')
true

julia> islowercase('Γ')
false

julia> islowercase('❤')
false
```
