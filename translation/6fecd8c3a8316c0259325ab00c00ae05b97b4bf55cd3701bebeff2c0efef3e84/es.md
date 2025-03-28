```
isdigit(c::AbstractChar) -> Bool
```

Prueba si un carácter es un dígito decimal (0-9).

Véase también: [`isletter`](@ref).

# Ejemplos

```jldoctest
julia> isdigit('❤')
false

julia> isdigit('9')
true

julia> isdigit('α')
false
```
