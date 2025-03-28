```
isxdigit(c::AbstractChar) -> Bool
```

Prueba si un carácter es un dígito hexadecimal válido. Ten en cuenta que esto no incluye `x` (como en el prefijo estándar `0x`).

# Ejemplos

```jldoctest
julia> isxdigit('a')
true

julia> isxdigit('x')
false
```
