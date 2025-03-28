```
x | y
```

O lógico. Implementa [lógica de tres valores](https://es.wikipedia.org/wiki/L%C3%B3gica_de_tres_valores), devolviendo [`missing`](@ref) si un operando es `missing` y el otro es `false`.

Véase también: [`&`](@ref), [`xor`](@ref), [`||`](@ref).

# Ejemplos

```jldoctest
julia> 4 | 10
14

julia> 4 | 1
5

julia> true | missing
true

julia> false | missing
missing
```
