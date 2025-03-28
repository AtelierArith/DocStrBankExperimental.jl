```
isuppercase(c::AbstractChar) -> Bool
```

Prueba si un carácter es una letra mayúscula (de acuerdo con la propiedad derivada `Uppercase` del estándar Unicode).

Véase también [`islowercase`](@ref).

# Ejemplos

```jldoctest
julia> isuppercase('γ')
false

julia> isuppercase('Γ')
true

julia> isuppercase('❤')
false
```
