```
ρ = crystal_density(crystal) # kg/m²
```

Compute the crystal density of a crystal. Pulls atomic masses from [`read_atomic_masses`](@ref).

# Arguments

  * `crystal::Crystal`: The crystal containing the crystal structure information

# Returns

  * `ρ::Float64`: The crystal density of a crystal in kg/m³  # –> kg/m3
