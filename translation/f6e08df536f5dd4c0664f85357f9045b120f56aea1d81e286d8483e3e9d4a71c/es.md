```
>>>(x, n)
```

Operador de desplazamiento de bits a la derecha sin signo, `x >>> n`. Para `n >= 0`, el resultado es `x` desplazado a la derecha por `n` bits, llenando con `0`s. Para `n < 0`, esto es equivalente a `x << -n`.

Para los tipos de enteros [`Unsigned`](@ref), esto es equivalente a [`>>`](@ref). Para los tipos de enteros [`Signed`](@ref), esto es equivalente a `signed(unsigned(x) >> n)`.

# Ejemplos

```jldoctest
julia> Int8(-14) >>> 2
60

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(60))
"00111100"
```

Los [`BigInt`](@ref)s se tratan como si tuvieran tamaño infinito, por lo que no se requiere llenado y esto es equivalente a [`>>`](@ref).

Véase también [`>>`](@ref), [`<<`](@ref).
