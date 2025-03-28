```
frexp(val)
```

Devuelve `(x,exp)` tal que `x` tiene una magnitud en el intervalo $[1/2, 1)$ o 0, y `val` es igual a $x \times 2^{exp}$.

Véase también [`significand`](@ref), [`exponent`](@ref), [`ldexp`](@ref).

# Ejemplos

```jldoctest
julia> frexp(6.0)
(0.75, 3)

julia> significand(6.0), exponent(6.0)  # intervalo [1, 2) en su lugar
(1.5, 2)

julia> frexp(0.0), frexp(NaN), frexp(-Inf)  # el exponente daría un error
((0.0, 0), (NaN, 0), (-Inf, 0))
```
