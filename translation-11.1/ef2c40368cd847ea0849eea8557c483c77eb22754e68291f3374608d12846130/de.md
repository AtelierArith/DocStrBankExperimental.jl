```
nextpow(a, x)
```

Die kleinste `a^n`, die nicht kleiner als `x` ist, wobei `n` eine nicht-negative ganze Zahl ist. `a` muss größer als 1 sein, und `x` muss größer als 0 sein.

Siehe auch [`prevpow`](@ref).

# Beispiele

```jldoctest
julia> nextpow(2, 7)
8

julia> nextpow(2, 9)
16

julia> nextpow(5, 20)
25

julia> nextpow(4, 16)
16
```
