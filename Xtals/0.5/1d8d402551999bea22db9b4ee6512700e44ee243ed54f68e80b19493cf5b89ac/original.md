```
box = Box(a, b, c, α, β, γ, volume, f_to_c, c_to_f, reciprocal_lattice)
box = Box(a, b, c, α, β, γ)
box = Box(a, b, c) # α=β=γ=π/2 assumed.
box = Box(f_to_c)
```

Data structure to describe a unit cell box (Bravais lattice) and convert between fractional and Cartesian coordinates.

# Attributes

  * `a,b,c::Float64`: unit cell dimensions (units: Angstroms)
  * `α,β,γ::Float64`: unit cell angles (units: radians)
  * `Ω::Float64`: volume of the unit cell (units: cubic Angtroms)
  * `f_to_c::Array{Float64,2}`: the 3x3 transformation matrix used to map fractional

coordinates to cartesian coordinates. The columns of this matrix define the unit cell axes. Columns are the vectors defining the unit cell box. units: Angstrom

  * `c_to_f::Array{Float64,2}`: the 3x3 transformation matrix used to map Cartesian

coordinates to fractional coordinates. units: inverse Angstrom

  * `reciprocal_lattice::Array{Float64, 2}`: the *rows* are the reciprocal lattice vectors.

This choice was made (instead of columns) for speed of Ewald Sums.
