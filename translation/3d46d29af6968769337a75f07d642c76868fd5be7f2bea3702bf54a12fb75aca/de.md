```
shuffle([rng=default_rng(),] v::AbstractArray)
```

Gibt eine zufällig permutierte Kopie von `v` zurück. Das optionale Argument `rng` gibt einen Zufallszahlengenerator an (siehe [Zufallszahlen](@ref)). Um `v` in-place zu permutieren, siehe [`shuffle!`](@ref). Um zufällig permutierte Indizes zu erhalten, siehe [`randperm`](@ref).

# Beispiele

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
