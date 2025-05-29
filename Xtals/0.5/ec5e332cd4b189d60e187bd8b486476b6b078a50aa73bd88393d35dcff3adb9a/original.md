```
crystal_with_charges = assign_charges(crystal, species_to_charge, net_charge_tol=1e-5)
```

assign charges to the atoms present in the crystal based on atom type. pass a dictionary `species_to_charge` that maps atomic species to a charge.

if the crystal already has charges, the charges are removed and new charges are added. a warning is thrown if this is the case.

checks for charge neutrality in the end.

returns a new crystal.

# Examples

```
species_to_charge = Dict(:Ca => 2.0, :C => 1.0, :H => -1.0)
crystal_with_charges = assign_charges(crystal, species_to_charge, 1e-7)
crystal_with_charges = assign_charges(crystal, species_to_charge) # tol 1e-5 default
```

# Arguments

  * `crystal::Crystal`: the crystal
  * `species_to_charge::Dict{Symbol, Float64}`: a dictionary that maps atomic species to charge
  * `net_charge_tol::Float64`: the net charge tolerated when asserting charge neutrality of the resulting crystal
