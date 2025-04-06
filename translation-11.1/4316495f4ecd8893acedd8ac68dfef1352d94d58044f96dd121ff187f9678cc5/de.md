```
sign(x)
```

Gibt null zurück, wenn `x==0` und $x/|x|$ andernfalls (d.h. ±1 für reelles `x`).

Siehe auch [`signbit`](@ref), [`zero`](@ref), [`copysign`](@ref), [`flipsign`](@ref).

# Beispiele

```jldoctest
julia> sign(-4.0)
-1.0

julia> sign(99)
1

julia> sign(-0.0)
-0.0

julia> sign(0 + im)
0.0 + 1.0im
```
