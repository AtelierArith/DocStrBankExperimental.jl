```
<<(x, n)
```

Operador de desplazamiento de bits a la izquierda, `x << n`. Para `n >= 0`, el resultado es `x` desplazado a la izquierda por `n` bits, llenando con `0`s. Esto es equivalente a `x * 2^n`. Para `n < 0`, esto es equivalente a `x >> -n`.

# Ejemplos

```jldoctest
julia> Int8(3) << 2
12

julia> bitstring(Int8(3))
"00000011"

julia> bitstring(Int8(12))
"00001100"
```

Ver también [`>>`](@ref), [`>>>`](@ref), [`exp2`](@ref), [`ldexp`](@ref).
