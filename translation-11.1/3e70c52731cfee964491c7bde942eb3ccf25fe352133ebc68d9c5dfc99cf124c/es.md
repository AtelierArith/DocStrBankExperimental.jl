```
 isidentifier(s) -> Bool
```

Devuelve si el símbolo o cadena `s` contiene caracteres que se interpretan como un identificador ordinario válido (no un operador binario/unario) en el código de Julia; véase también [`Base.isoperator`](@ref).

Internamente, Julia permite cualquier secuencia de caracteres en un `Symbol` (excepto `\0`s), y las macros utilizan automáticamente nombres de variables que contienen `#` para evitar colisiones de nombres con el código circundante. Para que el analizador reconozca una variable, utiliza un conjunto limitado de caracteres (ampliamente extendido por Unicode). `isidentifier()` hace posible consultar directamente al analizador si un símbolo contiene caracteres válidos.

# Ejemplos

```jldoctest
julia> Meta.isidentifier(:x), Meta.isidentifier("1x")
(true, false)
```
