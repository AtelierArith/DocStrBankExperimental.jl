```
x & y
```

Y bit a bit. Implementa [lógica de tres valores](https://es.wikipedia.org/wiki/L%C3%B3gica_de_tres_valores), devolviendo [`missing`](@ref) si un operando es `missing` y el otro es `true`. Agrega paréntesis para la forma de aplicación de función: `(&)(x, y)`.

Ver también: [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Ejemplos

```jldoctest
julia> 4 & 10
0

julia> 4 & 12
4

julia> true & missing
missing

julia> false & missing
false
```
