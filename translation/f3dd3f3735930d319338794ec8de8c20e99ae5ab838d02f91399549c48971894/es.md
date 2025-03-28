```
significand(x)
```

Extrae el significando (también conocido como mantisa) de un número de punto flotante. Si `x` es un número finito no cero, entonces el resultado será un número del mismo tipo y signo que `x`, y cuyo valor absoluto está en el intervalo $[1,2)$. De lo contrario, se devuelve `x`.

Véase también [`frexp`](@ref), [`exponent`](@ref).

# Ejemplos

```jldoctest
julia> significand(15.2)
1.9

julia> significand(-15.2)
-1.9

julia> significand(-15.2) * 2^3
-15.2

julia> significand(-Inf), significand(Inf), significand(NaN)
(-Inf, Inf, NaN)
```
