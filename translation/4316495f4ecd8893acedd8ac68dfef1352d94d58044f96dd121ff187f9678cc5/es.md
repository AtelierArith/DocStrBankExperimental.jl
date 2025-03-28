```
sign(x)
```

Devuelve cero si `x==0` y $x/|x|$ de lo contrario (es decir, ±1 para `x` real).

Véase también [`signbit`](@ref), [`zero`](@ref), [`copysign`](@ref), [`flipsign`](@ref).

# Ejemplos

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
