```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

Version en place de [`shuffle`](@ref) : permute aléatoirement `v` en place, en fournissant éventuellement le générateur de nombres aléatoires `rng`.

# Exemples

```jldoctest
julia> shuffle!(Xoshiro(123), Vector(1:10))
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
