```
bond_rules = bondingrules()
bond_rules = bondingrules(covalent_radii=covalent_radii(), pad=0.05)
```

Returns a set of bonding rules based on the given Cordero parameters and tolerances.

# Arguments

  * `cov_rad::Union{Dict{Symbol, Float64}, Nothing}`: Covalent radii. See [`covalent_radii()`](@ref)
  * `pad::Float`: Amount to pad covalent radii for bonding interactions.

# Returns

  * `bondingrules::Array{BondingRule, 1}`: Bonding rules from the specified covalent radii.`
