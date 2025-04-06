```
frexp(val)
```

Gibt `(x,exp)` zurück, so dass `x` eine Größe im Intervall $[1/2, 1)$ oder 0 hat, und `val` gleich $x \times 2^{exp}$ ist.

Siehe auch [`significand`](@ref), [`exponent`](@ref), [`ldexp`](@ref).

# Beispiele

```jldoctest
julia> frexp(6.0)
(0.75, 3)

julia> significand(6.0), exponent(6.0)  # Intervall [1, 2) stattdessen
(1.5, 2)

julia> frexp(0.0), frexp(NaN), frexp(-Inf)  # Exponent würde einen Fehler geben
((0.0, 0), (NaN, 0), (-Inf, 0))
```
