```
nearest_image!(dxf)
```

Applies the nearest image convention on a vector `dxf` between two atoms in fractional space; modifies `dxf` for nearest image convention. Fractional coordinates here fall in [0, 1] so that the box is [0, 1]^3 in fractional space.

Warning: this assumes the two molecules are in the box described by fractional coords [0, 1]³.

# Arguments

  * `dxf::Array{Float64}`: A vector between two atoms in fractional space
