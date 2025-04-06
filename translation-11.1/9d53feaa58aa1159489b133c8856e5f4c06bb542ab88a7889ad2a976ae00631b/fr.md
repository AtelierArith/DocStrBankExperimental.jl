```
randexp([rng=default_rng()], [T=Float64], [dims...])
```

Génère un nombre aléatoire de type `T` selon la distribution exponentielle avec une échelle de 1. Génère éventuellement un tableau de tels nombres aléatoires. Le module `Base` fournit actuellement une implémentation pour les types [`Float16`](@ref), [`Float32`](@ref) et [`Float64`](@ref) (le défaut).

# Exemples

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
