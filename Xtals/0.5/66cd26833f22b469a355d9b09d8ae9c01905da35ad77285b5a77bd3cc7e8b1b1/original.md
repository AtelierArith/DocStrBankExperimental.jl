used to represent a set of partial point charges in space (their charges and coordinates).

```julia
struct Charges{T <: Coords} # enforce that the type specified is `Coords`
    n::Int
    q::Array{Float64, 1}
    coords::T
end
```

here, `T` is `Frac` or `Cart`.

helper constructor (infers `n`):

```julia
q = [0.1, -0.1]
coords = Cart(rand(3, 2))
charges = Charges(q, coords)
```
