```
isequal_normalized(s1::AbstractString, s2::AbstractString; casefold=false, stripmark=false, chartransform=identity)
```

Devuelve si `s1` y `s2` son cadenas Unicode equivalentes de manera canónica. Si `casefold=true`, ignora mayúsculas y minúsculas (realiza un plegado de mayúsculas Unicode); si `stripmark=true`, elimina marcas diacríticas y otros caracteres combinantes.

Al igual que con [`Unicode.normalize`](@ref), también puedes pasar una función arbitraria a través de la palabra clave `chartransform` (mapeando puntos de código `Integer` a puntos de código) para realizar normalizaciones personalizadas, como [`Unicode.julia_chartransform`](@ref).

!!! compat "Julia 1.8"
    La función `isequal_normalized` se agregó en Julia 1.8.


# Ejemplos

Por ejemplo, la cadena `"noël"` se puede construir de dos maneras equivalentes de manera canónica en Unicode, dependiendo de si `"ë"` se forma a partir de un solo punto de código U+00EB o a partir del carácter ASCII `'e'` seguido del carácter combinante U+0308 diaeresis.

```jldoctest
julia> s1 = "noël"
"noël"

julia> s2 = "noël"
"noël"

julia> s1 == s2
false

julia> isequal_normalized(s1, s2)
true

julia> isequal_normalized(s1, "noel", stripmark=true)
true

julia> isequal_normalized(s1, "NOËL", casefold=true)
true
```
