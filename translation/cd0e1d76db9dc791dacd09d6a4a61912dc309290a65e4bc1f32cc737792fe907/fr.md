```
exponent(x::Real) -> Int
```

Renvoie le plus grand entier `y` tel que `2^y ≤ abs(x)`.

Lève une `DomainError` lorsque `x` est zéro, infini, ou [`NaN`](@ref). Pour tout autre nombre à virgule flottante non subnormal `x`, cela correspond aux bits d'exposant de `x`.

Voir aussi [`signbit`](@ref), [`significand`](@ref), [`frexp`](@ref), [`issubnormal`](@ref), [`log2`](@ref), [`ldexp`](@ref).

# Exemples

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
