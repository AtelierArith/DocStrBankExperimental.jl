```
sign(x)
```

Retourne zéro si `x==0` et $x/|x|$ sinon (c'est-à-dire, ±1 pour `x` réel).

Voir aussi [`signbit`](@ref), [`zero`](@ref), [`copysign`](@ref), [`flipsign`](@ref).

# Exemples

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
