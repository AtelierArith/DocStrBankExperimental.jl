used to represent a set of atoms in space (their atomic species and coordinates).

```julia
struct Atoms{T <: Coords} # enforce that the type specified is `Coords`
    n::Int # how many atoms?
    species::Array{Symbol, 1} # list of species
    coords::T # coordinates
end
```

here, `T` is `Frac` or `Cart`.

helper constructor (infers `n`):

```julia
species = [:H, :H]
coords = Cart(rand(3, 2))
atoms = Atoms(species, coords)
```
