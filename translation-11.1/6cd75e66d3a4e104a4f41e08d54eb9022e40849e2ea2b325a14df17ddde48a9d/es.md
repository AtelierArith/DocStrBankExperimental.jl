```
rpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

Convierte `s` a una cadena y rellena la cadena resultante a la derecha con `p` para que tenga `n` caracteres (en [`textwidth`](@ref)). Si `s` ya tiene `n` caracteres de longitud, se devuelve una cadena igual. Por defecto, se rellena con espacios.

# Ejemplos

```jldoctest
julia> rpad("March", 20)
"March               "
```

!!! compat "Julia 1.7"
    En Julia 1.7, esta función se cambió para usar `textwidth` en lugar de un conteo de caracteres (puntos de código) en bruto.

