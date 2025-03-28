```
prevpow(a, x)
```

El mayor `a^n` que no es mayor que `x`, donde `n` es un entero no negativo. `a` debe ser mayor que 1, y `x` no debe ser menor que 1.

Véase también [`nextpow`](@ref), [`isqrt`](@ref).

# Ejemplos

```jldoctest
julia> prevpow(2, 7)
4

julia> prevpow(2, 9)
8

julia> prevpow(5, 20)
5

julia> prevpow(4, 16)
16
```
