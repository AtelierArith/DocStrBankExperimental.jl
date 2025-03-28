```
isnumeric(c::AbstractChar) -> Bool
```

Prueba si un carácter es numérico. Un carácter se clasifica como numérico si pertenece a la categoría general de Unicode Número, es decir, un carácter cuyo código de categoría comienza con 'N'.

Ten en cuenta que esta amplia categoría incluye caracteres como ¾ y ௰. Usa [`isdigit`](@ref) para verificar si un carácter es un dígito decimal entre 0 y 9.

# Ejemplos

```jldoctest
julia> isnumeric('௰')
true

julia> isnumeric('9')
true

julia> isnumeric('α')
false

julia> isnumeric('❤')
false
```
