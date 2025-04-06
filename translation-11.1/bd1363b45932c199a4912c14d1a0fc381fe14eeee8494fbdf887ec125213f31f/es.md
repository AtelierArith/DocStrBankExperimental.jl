```
isletter(c::AbstractChar) -> Bool
```

Prueba si un carácter es una letra. Un carácter se clasifica como letra si pertenece a la categoría general de Unicode Letra, es decir, un carácter cuyo código de categoría comienza con 'L'.

Véase también: [`isdigit`](@ref).

# Ejemplos

```jldoctest
julia> isletter('❤')
false

julia> isletter('α')
true

julia> isletter('9')
false
```
