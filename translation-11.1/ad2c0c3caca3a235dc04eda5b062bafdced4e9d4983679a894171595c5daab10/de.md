```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

In-Place-Version von [`shuffle`](@ref): permutiert `v` zufällig in-place, wobei optional der Zufallszahlengenerator `rng` angegeben werden kann.

# Beispiele

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
