```
ispow2(n::Number) -> Bool
```

Prueba si `n` es una potencia entera de dos.

Véase también [`count_ones`](@ref), [`prevpow`](@ref), [`nextpow`](@ref).

# Ejemplos

```jldoctest
julia> ispow2(4)
true

julia> ispow2(5)
false

julia> ispow2(4.5)
false

julia> ispow2(0.25)
true

julia> ispow2(1//8)
true
```

!!! compat "Julia 1.6"
    El soporte para argumentos no `Integer` se agregó en Julia 1.6.

