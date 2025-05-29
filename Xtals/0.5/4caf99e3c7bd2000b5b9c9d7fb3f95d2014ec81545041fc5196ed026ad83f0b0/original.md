cartesian coordinates, a subtype of `Coords`.

construct by passing an `Array{Float64, 2}` whose columns are the coordinates.

e.g.

```julia
c_coords = Cart(rand(3, 2))  # 2 particles
c_coords.x                   # retreive cartesian coords
```
