```
exponent(x::Real) -> Int
```

Devuelve el mayor entero `y` tal que `2^y ≤ abs(x)`.

Lanza un `DomainError` cuando `x` es cero, infinito, o [`NaN`](@ref). Para cualquier otro número de punto flotante no subnormal `x`, esto corresponde a los bits del exponente de `x`.

Véase también [`signbit`](@ref), [`significand`](@ref), [`frexp`](@ref), [`issubnormal`](@ref), [`log2`](@ref), [`ldexp`](@ref).

# Ejemplos

```jldoctest
julia> exponent(8)
3

julia> exponent(6.5)
2

julia> exponent(-1//4)
-2

julia> exponent(3.142e-4)
-12

julia> exponent(floatmin(Float32)), exponent(nextfloat(0.0f0))
(-126, -149)

julia> exponent(0.0)
ERROR: DomainError with 0.0:
Cannot be ±0.0.
[...]
```
