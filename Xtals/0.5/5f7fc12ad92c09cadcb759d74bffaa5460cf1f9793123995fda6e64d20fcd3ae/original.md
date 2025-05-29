fractional coordinates, a subtype of `Coords`.

construct by passing an `Array{Float64, 2}` whose columns are the coordinates.

generally, fractional coordinates should be in [0, 1] and are implicitly associated with a `Box` to represent a periodic coordinate system.

e.g.

```julia
f_coords = Frac(rand(3, 2))  # 2 particles
f_coords.xf                  # retreive fractional coords
```
