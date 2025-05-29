```
simulation_ready_crystal = apply_symmetry_operations(non_p1_crystal)
```

Convert a crystal to P1 symmetry based on internal symmetry rules. This will return a new crystal.

# Arguments

  * `non_p1_crystal::Crystal`: The crystal to be converted to P1 symmetry

# Returns

  * `P1_crystal::Crystal`: The crystal after it has been converted to P1 symmetry. The new symmetry rules will be the P1 symmetry rules
