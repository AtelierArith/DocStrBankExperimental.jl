```
string(n::Integer; base::Integer = 10, pad::Integer = 1)
```

Convierte un entero `n` a una cadena en la `base` dada, especificando opcionalmente un número de dígitos para rellenar.

Véase también [`digits`](@ref), [`bitstring`](@ref), [`count_zeros`](@ref).

# Ejemplos

```jldoctest
julia> string(5, base = 13, pad = 4)
"0005"

julia> string(-13, base = 5, pad = 4)
"-0023"
```
