```
exponent(x::Real) -> Int
```

Gibt die größte ganze Zahl `y` zurück, so dass `2^y ≤ abs(x)`.

Wirft einen `DomainError`, wenn `x` null, unendlich oder [`NaN`](@ref) ist. Für jede andere nicht-subnormale Fließkommazahl `x` entspricht dies den Exponentenbits von `x`.

Siehe auch [`signbit`](@ref), [`significand`](@ref), [`frexp`](@ref), [`issubnormal`](@ref), [`log2`](@ref), [`ldexp`](@ref).

# Beispiele

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
ERROR: DomainError mit 0.0:
Kann nicht ±0.0 sein.
[...]
```
