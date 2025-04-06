```
isvalid(s::AbstractString, i::Integer) -> Bool
```

Predicado que indica si el índice dado es el inicio de la codificación de un carácter en `s` o no. Si `isvalid(s, i)` es verdadero, entonces `s[i]` devolverá el carácter cuya codificación comienza en ese índice; si es falso, entonces `s[i]` generará un error de índice no válido o un error de límites dependiendo de si `i` está dentro de los límites. Para que `isvalid(s, i)` sea una función O(1), la codificación de `s` debe ser [auto-sincronizadora](https://en.wikipedia.org/wiki/Self-synchronizing_code). Esta es una suposición básica del soporte de cadenas genéricas de Julia.

Véase también [`getindex`](@ref), [`iterate`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref), [`length`](@ref).

# Ejemplos

```jldoctest
julia> str = "αβγdef";

julia> isvalid(str, 1)
true

julia> str[1]
'α': Unicode U+03B1 (categoría Ll: Letra, minúscula)

julia> isvalid(str, 2)
false

julia> str[2]
ERROR: StringIndexError: índice no válido [2], índices cercanos válidos [1]=>'α', [3]=>'β'
Stacktrace:
[...]
```
