```
prevpow(a, x)
```

Die größte `a^n`, die nicht größer als `x` ist, wobei `n` eine nicht-negative ganze Zahl ist. `a` muss größer als 1 sein, und `x` darf nicht kleiner als 1 sein.

Siehe auch [`nextpow`](@ref), [`isqrt`](@ref).

# Beispiele

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
