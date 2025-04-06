```
shuffle([rng=default_rng(),] v::AbstractArray)
```

Retourne une copie de `v` permutée aléatoirement. L'argument optionnel `rng` spécifie un générateur de nombres aléatoires (voir [Nombres aléatoires](@ref)). Pour permuter `v` sur place, voir [`shuffle!`](@ref). Pour obtenir des indices permutés aléatoirement, voir [`randperm`](@ref).

# Exemples

```jldoctest
julia> shuffle(Xoshiro(123), Vector(1:10))
10-element Vector{Int64}:
  5
  4
  2
  3
  6
 10
  8
  1
  9
  7
```
