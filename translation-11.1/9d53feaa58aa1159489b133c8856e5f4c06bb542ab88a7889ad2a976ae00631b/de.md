```
randexp([rng=default_rng()], [T=Float64], [dims...])
```

Generiert eine Zufallszahl vom Typ `T` gemäß der Exponentialverteilung mit einer Skala von 1. Optional kann ein Array solcher Zufallszahlen generiert werden. Das `Base`-Modul bietet derzeit eine Implementierung für die Typen [`Float16`](@ref), [`Float32`](@ref) und [`Float64`](@ref) (der Standard).

# Beispiele

```jldoctest
julia> rng = Xoshiro(123);

julia> randexp(rng, Float32)
1.1757717f0

julia> randexp(rng, 3, 3)
3×3 Matrix{Float64}:
 1.37766  0.456653  0.236418
 3.40007  0.229917  0.0684921
 0.48096  0.577481  0.71835
```
